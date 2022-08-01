<template>
  <Sidebar />
  <main v-bind:style="{ 'margin-left': sidebarWidth }">
    <router-view />
  </main>
</template>

<script>
import Sidebar from './components/sidebar/Sidebar.vue'
import { sidebarWidth } from './components/sidebar/state'
export default {
  components: {
    Sidebar
  },
  setup() {
    return {
      sidebarWidth
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

main {
  transition: 0.2s ease;
}
</style>