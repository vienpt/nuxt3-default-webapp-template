<script setup lang="ts">
const links = [
  ['mdi-inbox-arrow-down', 'Inbox'],
  ['mdi-send', 'Send'],
  ['mdi-delete', 'Trash'],
  ['mdi-alert-octagon', 'Spam'],
]
</script>

<template>
  <div class="dynamic-nav">
      <v-navigation-drawer
          width="320"
          color="grey-lighten-5"
          @mouseleave="$emit('close', 'mdi-menu')">
        <v-sheet
            height="48"
            width="100%"
            class="workspace"
            color="grey-lighten-5"
            @click="navigateTo('/')"
        >
          <v-list-item prepend-icon="mdi-account">
            <v-list-item-title>vien workspace</v-list-item-title>
          </v-list-item>
        </v-sheet>

        <v-list>
          <v-list-item
              v-for="[icon, text] in links"
              :key="icon"
              :prepend-icon="icon"
              :title="text"
              link
              @click="$emit('navigate', text)"
          ></v-list-item>
        </v-list>
      </v-navigation-drawer>
  </div>

</template>

<style scoped>
.dynamic-nav {
  transition: opacity 0.3s;
}
</style>