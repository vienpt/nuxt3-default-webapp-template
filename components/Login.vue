<template>
  <v-list>
    <VListItem @click="$emit('navigate', 'login')">
      <template #default>
        <v-icon>mdi-account</v-icon>
        Login
      </template>
    </VListItem>
  </v-list>
</template>

<script setup lang="ts">
defineEmits(['navigate'])
</script>

<script lang="ts">
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Login',
};
</script>