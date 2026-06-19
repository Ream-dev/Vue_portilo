<template>
  <section>
    <a href="/projects" class="back-link">← Back to Projects</a>
    <div v-if="!project">
      <h1 class="page-title">Project <span class="accent">not found</span></h1>
      <p class="page-subtitle">No project exists with ID "{{ projectId }}".</p>
    </div>
    <div v-else>
      <div class="detail-meta">
        <span class="card-tag">{{ project.tag }}</span>
        <span style="color: var(--muted); font-size: 0.85rem">Project #{{ project.id }}</span>
      </div>
      <h1 class="page-title">{{ project.title }}</h1>
      <p class="page-subtitle">{{ project.summary }}</p>
      <div class="detail-body">
        <p v-for="(para, i) in project.body" :key="i">{{ para }}</p>
      </div>
      <div class="tech-list">
        <span class="tech-pill" v-for="t in project.tech" :key="t">{{ t }}</span>
      </div>
    </div>
  </section>
</template>
<script setup>
import { computed } from 'vue'
import { useRoute } from 'vue-router'
import { projects } from './ProjectsView.vue'
const projectId = 0
const project = null
</script>
