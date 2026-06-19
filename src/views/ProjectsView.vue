<template>
  <section>
    <h1 class="page-title">My <span class="accent">Projects</span></h1>
    <p class="page-subtitle">
      Click any project to see its detail page — that's your dynamic route in action!
    </p>

    <div class="card-grid">
      <div class="card" v-for="project in projects" :key="project.id">
        <span class="card-tag">{{ project.tag }}</span>
        <h3>{{ project.title }}</h3>
        <p>{{ project.summary }}</p>
      </div>
    </div>
  </section>
</template>

<script setup>
export const projects = [
  {
    id: 1,
    tag: 'Vue 3',
    title: 'Weather Dashboard',
    summary: 'A reactive weather app pulling live data from an open API.',
    tech: ['Vue 3', 'Pinia', 'OpenWeatherMap API', 'Chart.js'],
    body: [
      'Built with the Composition API and Pinia for state management, this dashboard displays current conditions, hourly forecasts, and a 7-day outlook for any city worldwide.',
      'The project taught me how to manage async data fetching, handle error states gracefully, and create smooth chart animations with Chart.js integration.',
    ],
  },
  {
    id: 2,
    tag: 'Full-Stack',
    title: 'Task Manager API',
    summary: 'RESTful API with authentication, built on Node + Express.',
    tech: ['Node.js', 'Express', 'PostgreSQL', 'JWT'],
    body: [
      'A full-featured REST API that supports user accounts, task CRUD operations, labels, due dates, and priority levels. JWT-based auth with refresh token rotation.',
      'Deployed on Railway with a PostgreSQL database. Includes automated tests written with Jest and Supertest.',
    ],
  },
  {
    id: 3,
    tag: 'CSS',
    title: 'Component Library',
    summary: 'A hand-crafted design system with 20+ Vue components.',
    tech: ['Vue 3', 'Storybook', 'CSS Custom Properties', 'Rollup'],
    body: [
      'Designed and built from scratch — no Tailwind, no UI kit. Every component (buttons, modals, toasts, data tables) is documented in Storybook with live examples.',
      'Bundled as an npm package so I can drop it into any Vue project. Theme switching via CSS custom properties at the root level.',
    ],
  },
  {
    id: 4,
    tag: 'WebSockets',
    title: 'Live Chat App',
    summary: 'Real-time messaging with rooms, typing indicators, and presence.',
    tech: ['Vue 3', 'Socket.io', 'Express', 'Redis'],
    body: [
      'Uses Socket.io on both client and server to handle room-based messaging, online/offline presence, and live typing indicators with debounce.',
      'Redis pub/sub allows the Node server to scale horizontally — messages publish to a shared channel so all instances stay in sync.',
    ],
  },
]
</script>
