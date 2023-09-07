<template>
  <v-app id="inspire">
<!--    sidebar-->
    <Transition name="sidebar" appear>
      <Nav
          v-if="nav"
          :isShowChevronIcon="false"
          @toggleDynamicNav="toggleDynamicNav"
          @navigate="(link) => navigateTo(link)"
      />
    </Transition>


    <v-app-bar
        class="px-3"
        color="grey-lighten-5"
        flat
        height="48"
    >

      <v-btn
          v-if="isShowDynamicMenu"
          class="burger-hover-menu"
          variant="text"
          :icon="dynamicIcon"
          @click.stop="toggleNavMenu"
          @mouseleave.one="!dynamicNav"
          @mouseenter="dynamicIcon = 'mdi-chevron-double-right'"
      ></v-btn>
      <v-list-item-title class="header-title">Reading List</v-list-item-title>
    </v-app-bar>

<!--    content-->
    <v-main>
      <Transition name="dynamic-transition">
        <DynamicNav
            v-if="dynamicNav ?? defaultDynamicNav"
            @close="(val) => dynamicIcon = val"
            @navigate="(link) => navigateTo(link)"
        />
      </Transition>

      <VContainer>
        <NuxtPage />
      </VContainer>
    </v-main>
  </v-app>
</template>

<script setup lang="ts">
type DYNAMICICON = 'mdi-chevron-double-right' | 'mdi-format-align-justify'

const nav = ref(true)
const isShowDynamicMenu = ref(false)

const drawerHover = ref(false)
const dynamicIcon = ref<DYNAMICICON>('mdi-format-align-justify')
const dynamicNav = computed(() => dynamicIcon.value !== 'mdi-format-align-justify')
const defaultDynamicNav = computed(() => isShowDynamicMenu.value && dynamicIcon.value === 'mdi-chevron-double-right')

watch(() => defaultDynamicNav.value, (val) => {
  console.log('val', val)
})

function toggleDynamicNav() {
  nav.value = false
  isShowDynamicMenu.value = true
  dynamicIcon.value = 'mdi-chevron-double-right'
}

function toggleNavMenu() {
  nav.value = true
  isShowDynamicMenu.value = false
  dynamicIcon.value = 'mdi-format-align-justify'
}
</script>

<style>
.workspace:hover {
  background-color: #f6f6f6;
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

/**
dynamic transition
 */
.dynamic-transition-enter-active {
  animation: slideIn 0.5s;
}
@keyframes slideIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.dynamic-transition-leave-active {
  animation: slideOut 0.3s reverse;
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