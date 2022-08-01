<template>
  <router-link v-bind:to="to" class="link" v-bind:class="{ 'active' : isActive }">
    <i class="icon" v-bind:class="icon" />
    <transition name="fade">
      <span v-if="! collapsed">
        <slot />
      </span>
    </transition>
  </router-link>
</template>

<script>
import { computed } from 'vue'
import { useRoute } from 'vue-router'
import { collapsed } from './state'

export default {
  props: {
    to: {
      type: String,
      required: true
    },
    icon: {
      type: String,
      required: true
    }
  },
  setup(props) {
    const route = useRoute()
    const isActive = computed(() => route.path === props.to)

    return {
      collapsed,
      isActive
    }
  }
} 
</script>

<style scoped>
.link {
  display: flex;
  align-items: center;
  cursor: pointer;
  position: relative;
  font-weight: 400;
  user-select: none;
  color: #ffffff;
  text-decoration: none;
  margin: 0;
  padding: 0.4em;
  border-radius: 0.25em;
  height: 1.5em;
}
.link:hover {
  background-color: var(--sidebar-item-hover);
}
.link.active {
  background-color: var(--sidebar-item-active);
}
.link .icon {
  flex-shrink: 0;
  width: 25px;
  margin-right: 10px;
}
.fade-enter-active, .fade-leave-active {
  transition: opacity 0.1s;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>