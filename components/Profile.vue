<template>
  <v-list>
    <v-list-item @click="$emit('navigate', 'profile')">
      <template #default>
        <v-icon>mdi-account</v-icon>
        Profile
      </template>
    </v-list-item>
  </v-list>
</template>

<script setup lang="ts">

</script>

<script lang="ts">
export default {
  // eslint-disable-next-line vue/multi-word-component-names
  name: 'Profile',
};
</script>