<template>
  <header>Practice TypeScript with Nuxt 3</header>
  <div>
    <slot />
  </div>
</template>

<script setup lang="ts"></script>

<style scoped>
header {
  text-align: center;
  font-size: 40px;
  font-weight: 800;
  padding: 0.8em 0.5em;
  background: rgba(128, 128, 128, 0.519);
}
</style>
