<script setup lang="ts">
import {DYNAMICICON} from "~/types";

defineEmits(['toggleDrawerMenu'])
const props = defineProps({
  isShowBuggerMenu: {
    type: Boolean,
    default: false
  },
})

const dynamicIcon = ref<DYNAMICICON>('mdi-menu')

</script>

<template>
  <v-app-bar
    class="px-3"
    color="grey-darken-5"
    :flat="true"
    height="48"
  >
    <v-btn
      v-if="props.isShowBuggerMenu"
      class="burger-hover-menu"
      variant="text"
      :icon="dynamicIcon"
      @click.stop="$emit('toggleDrawerMenu')"
      @mouseenter="dynamicIcon = 'mdi-chevron-double-right'"
      @mouseleave="dynamicIcon = 'mdi-menu'"
    />
    <v-list-item-title class="header-title">
      Reading List
    </v-list-item-title>

    <v-spacer />

    <Login @navigate="(path) => navigateTo(path)" />
  </v-app-bar>
</template>

<style scoped>

</style>