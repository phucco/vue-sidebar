<template>
  <div class="sidebar" v-bind:style="{ 'width': sidebarWidth }">
    <h1>
      <span v-if="collapsed">
        <div>V</div>
        <div>S</div>
      </span>
      <span v-else>Vue Sidebar</span>
    </h1>
    
    <SidebarLink to="/" icon="fas fa-home">Home</SidebarLink>
    <SidebarLink to="/dashboard" icon="fas fa-columns">Dashboard</SidebarLink>
    <SidebarLink to="/analytics" icon="fas fa-chart-bar">Analytics</SidebarLink>
    <SidebarLink to="/friends" icon="fas fa-users">Friends</SidebarLink>
    <SidebarLink to="/image" icon="fas fa-image">Images</SidebarLink>

    <span class="collapse-icon" v-on:click="toggleSidebar" v-bind:class="{ 'rotate-180' : collapsed }">
      <i class="fas fa-angle-double-left" />
    </span>
  </div>
</template>

<script>
import { collapsed, toggleSidebar, sidebarWidth } from './state'
import SidebarLink from './SidebarLink.vue'

export default {
  components: {
    SidebarLink
  },
  setup() {
    return {
      collapsed,
      toggleSidebar,
      sidebarWidth
    }
  }
}
</script>

<style>
:root {
  --sidebar-bg-color: #2f855a;
  --sidebar-item-hover: #38a169;
  --sidebar-item-active: #276749;
}
.sidebar {
  display: flex;
  flex-direction: column;
  color: #ffffff;
  background-color: var(--sidebar-bg-color);
  float: left;
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  z-index: 1;
  padding: 0.5em;
  transition: 0.3s ease;
}
.collapse-icon {
  position: absolute;
  bottom: 0;
  cursor: pointer;
  padding: 0.75em;
  color: #eeeeee;
  transition: 0.2s linear;
}
.collapse-icon:hover {
  color: #bbbbbb;
}
.rotate-180 {
  transform: rotate(180deg);
  transition: 0.2s linear;
}
</style>