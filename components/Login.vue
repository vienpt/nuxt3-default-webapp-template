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

</script>

<script lang="ts">
export default {
  name: 'Login',
};
</script>