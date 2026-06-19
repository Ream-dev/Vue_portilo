<template>
  <section>
    <p class="eyebrow">👋 Welcome to the exercise</p>
    <h1 class="page-title">
      Build a SPA with<br /><span class="accent">Vue Router</span>
    </h1>
    <p class="page-subtitle">
      This starter app has four pages to wire up. Your mission: connect every
      route, make the nav active-aware, and handle page not found — without
      a single full page reload.
    </p>

    <div class="card-grid">
      <div class="card" v-for="task in tasks" :key="task.id">
        <span class="card-tag">{{ task.file }}</span>
        <h3>{{ task.title }}</h3>
        <p>{{ task.desc }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
const tasks = [
  {
    id: 1,
    file: 'router/index.js',
    title: 'TODO 1–5: Define your routes',
    desc: 'Import the missing views and add routes for /projects, /projects/:id, and the 404 catch-all.',
  },
  {
    id: 2,
    file: 'App.vue',
    title: 'TODO 6: Swap <a> for <router-link>',
    desc: 'Replace the plain anchor tags in the nav with <router-link> so navigation stays within the SPA.',
  },
  {
    id: 3,
    file: 'views/ProjectDetail.vue',
    title: 'TODO 7: Read $route.params',
    desc: 'Inside ProjectDetail, use useRoute() to grab the :id param and display the matching project.',
  },
  {
    id: 4,
    file: 'views/NotFoundView.vue',
    title: 'TODO 8: Build the 404 page',
    desc: 'Create a friendly "Page Not Found" component and hook it up to the catch-all route.',
  },
]
</script>

<style scoped>
.eyebrow {
  font-size: 0.9rem;
  color: var(--muted);
  margin-bottom: 0.5rem;
  letter-spacing: 0.02em;
}
</style>
