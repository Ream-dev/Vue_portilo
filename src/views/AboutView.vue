<template>
  <section>
    <h1 class="page-title">About <span class="accent">Me</span></h1>
    <p class="page-subtitle">
      A passionate developer who loves building things on the web.
      This page is already wired up — use it as a reference when adding the
      remaining routes.
    </p>

    <div class="about-grid">
      <div class="about-card" v-for="item in skills" :key="item.label">
        <span class="about-icon">{{ item.icon }}</span>
        <strong>{{ item.label }}</strong>
        <p>{{ item.desc }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
const skills = [
  { icon: '⚡', label: 'Vue 3', desc: 'Composition API, reactivity, SFCs' },
  { icon: '🗺️', label: 'Vue Router 4', desc: 'History mode, dynamic routes, guards' },
  { icon: '🎨', label: 'CSS', desc: 'Custom properties, Grid, animations' },
  { icon: '🛠️', label: 'Vite', desc: 'Lightning-fast dev server & bundler' },
]
</script>

<style scoped>
.about-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(220px, 1fr));
  gap: 1rem;
}
.about-card {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: var(--radius);
  padding: 1.5rem;
}
.about-icon { font-size: 1.75rem; display: block; margin-bottom: 0.5rem; }
.about-card strong { display: block; margin-bottom: 0.3rem; font-family: var(--font-display); }
.about-card p { color: var(--muted); font-size: 0.875rem; }
</style>
