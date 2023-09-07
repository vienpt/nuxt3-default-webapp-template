<script lang="ts">
export default {
  // eslint-disable-next-line vue/no-reserved-component-names,vue/multi-word-component-names
  name: 'Nav',
};
</script>

<script setup lang="ts">
const props = defineProps({
  isShowChevronIcon: {
    type: Boolean,
    default: false
  }
})

defineEmits(['navigate', 'toggleDynamicNav'])

const isChevron = ref(props.isShowChevronIcon)
const links = [
  ['mdi-inbox-arrow-down', 'Inbox'],
  ['mdi-send', 'Send'],
  ['mdi-delete', 'Trash'],
  ['mdi-alert-octagon', 'Spam'],
]

function showChevronMenu() {
  isChevron.value = !isChevron.value
}

</script>

<template>
  <div class="sidebar-nav">
    <v-navigation-drawer
      color="grey-lighten-5"
      width="320"
    >
      <v-sheet
        height="48"
        width="100%"
        class="workspace"
        color="grey-lighten-5"
        @mouseenter="showChevronMenu"
        @mouseleave="showChevronMenu"
        @click="navigateTo('/')"
      >
        <v-list-item prepend-icon="mdi-account">
          <v-list-item-title>vien workspace</v-list-item-title>
        </v-list-item>

        <v-btn
          v-if="isChevron"
          class="bugger-drawer-menu"
          variant="text"
          icon="mdi-chevron-double-left"
          @click.stop="$emit('toggleDynamicNav')"
        />
      </v-sheet>

      <v-list>
        <v-list-item
          v-for="[icon, text] in links"
          :key="icon"
          :prepend-icon="icon"
          :title="text"
          :link="true"
          @click="$emit('navigate', text)"
        />
      </v-list>
    </v-navigation-drawer>
  </div>
</template>

<style scoped>
.bugger-drawer-menu {
  position: absolute;
  right: 0;
  top: 0;
}

.sidebar-nav {
  transition: opacity 0.5s;
}
</style>