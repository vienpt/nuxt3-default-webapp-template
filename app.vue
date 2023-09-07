<template>
  <v-app id="inspire">
    <!-- sidebar -->
    <Transition
      name="sidebar"
      appear
    >
      <Nav
        v-if="nav"
        :is-show-chevron-icon="false"
        @toggle-dynamic-nav="toggleDrawerMenu"
        @navigate="(link) => navigateTo(link)"
      />
    </Transition>

    <!-- Header -->
    <AppBar
      :is-show-bugger-menu="isShowBuggerMenu"
      @toggle-drawer-menu="toggleDrawerMenu"
    />

    <!-- content -->
    <v-main>
      <VContainer>
        <NuxtPage />
      </VContainer>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
const nav = ref(true)
const isShowBuggerMenu= ref(false)

function toggleDrawerMenu() {
  nav.value = !nav.value
  isShowBuggerMenu.value = !isShowBuggerMenu.value
}
</script>

<style>
.workspace:hover {
  background-color: #f6f6f6 !important;
}

.v-sheet {
  cursor: pointer !important;
}

.burger-hover-menu {
  left: -20px;
}

/**
sidebar transition
 */

.sidebar-enter-active {
  animation: sideBarAdded 0.5s;
}
@keyframes sideBarAdded {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
.sidebar-leave-active {
  animation: slideOut 0.5s reverse;
}

@keyframes slideOut {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}
</style>