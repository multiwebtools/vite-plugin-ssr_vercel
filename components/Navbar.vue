<template>
  <div class="navbar bg-base-100">
    <div class="navbar-start">
      <div class="dropdown">
        <label tabindex="0" class="btn btn-ghost btn-circle">
          <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h7" />
          </svg>
        </label>
        <ul tabindex="0" class="p-2 mt-3 shadow menu menu-compact dropdown-content bg-base-100 rounded-box w-52">
          <ul class="menu bg-base-100" v-for="category of Object.keys(state.toolsByCategory)" :key="category">
            <li tabindex="0">
              <span>{{ category }}</span>
              <ul class="bg-base-100">
                <li v-for="tool of state.toolsByCategory[category]" :key="tool.id"><a :href="tool.url">{{ tool.title
                }}</a></li>
              </ul>
            </li>
          </ul>

        </ul>

      </div>
    </div>
    <div class="navbar-center">
      <img class="w-32" src="../assets/logo.webp" alt="Multi Web Tools Logo">
    </div>
    <div class="navbar-end">

      <!-- <button class="btn btn-ghost btn-circle">
      <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 21l-6-6m2-5a7 7 0 11-14 0 7 7 0 0114 0z" /></svg>
    </button>
    <button class="btn btn-ghost btn-circle">
      <div class="indicator">
        <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 17h5l-1.405-1.405A2.032 2.032 0 0118 14.158V11a6.002 6.002 0 00-4-5.659V5a2 2 0 10-4 0v.341C7.67 6.165 6 8.388 6 11v3.159c0 .538-.214 1.055-.595 1.436L4 17h5m6 0v1a3 3 0 11-6 0v-1m6 0H9" /></svg>
        <span class="badge badge-xs badge-primary indicator-item"></span>
      </div>
    </button> -->
    </div>
  </div>
</template>

<script>
import { reactive } from 'vue'
import tools from '../tools'


const toolsByCategory = tools.reduce((acc, tool) => {
  acc[tool.category] = acc[tool.category] || []
  acc[tool.category].push(tool)
  return acc
}, {})

export default {
  setup(props) {
    const state = reactive({
      toolsByCategory,
    })
    return {
      state,
    }
  },
}
</script>
