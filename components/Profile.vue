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
  name: 'Profile',
};
</script>