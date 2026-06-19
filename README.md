# Vue Router Portfolio Exercise 🗺️

A hands-on starter project to master **Vue Router 4** fundamentals by building a mini Portfolio/Blog SPA.

---

## Getting Started

```bash
npm install
npm run dev
```

Open `http://localhost:5173` — you should see the home page with your task list.

---

## What You're Building

A single-page application with these routes:

| URL | Page | Status |
|-----|------|--------|
| `/` | Home | ✅ Done |
| `/about` | About | ✅ Done |
| `/projects` | Projects list | 🔧 Your job |
| `/projects/:id` | Project detail | 🔧 Your job |
| `/*` (anything else) | 404 Not Found | 🔧 Your job |

---

## Step-by-Step Instructions

Work through the TODOs **in order** — each one builds on the last.

---

### Step 1 — Import missing views (`router/index.js`)

Open `src/router/index.js`. You'll find `TODO 1` near the top.

Import the three remaining view components:

```js
import ProjectsView  from '../views/ProjectsView.vue'
import ProjectDetail from '../views/ProjectDetail.vue'
import NotFoundView  from '../views/NotFoundView.vue'
```

> **Why?** The router needs to know which component to render for each URL. You can't route to something that isn't imported.

---

### Step 2 — Add three routes (`router/index.js`)

Find `TODO 2`, `3`, and `4` inside the `routes` array. Add:

**TODO 2 — Projects list:**
```js
{
  path: '/projects',
  name: 'Projects',
  component: ProjectsView,
},
```

**TODO 3 — Dynamic project detail (the key concept!):**
```js
{
  path: '/projects/:id',
  name: 'ProjectDetail',
  component: ProjectDetail,
},
```

The `:id` is a **dynamic segment**. When a user visits `/projects/3`, Vue Router captures `3` as `route.params.id`.

**TODO 4 — Catch-all 404:**
```js
{
  path: '/:pathMatch(.*)*',
  name: 'NotFound',
  component: NotFoundView,
},
```

The `/:pathMatch(.*)*` pattern matches _every_ URL that no other route claimed. Always put this **last** in your routes array.

> ✅ **Check:** Visit `/projects` and `/this-page-is-fake` in your browser — what happens?

---

### Step 3 — Fix the navigation (`App.vue`)

Open `src/App.vue` and find `TODO 6`.

Replace every `<a href="...">` with `<router-link to="...">`:

```html
<!-- Before (causes a full page reload!) -->
<a href="/about">About</a>

<!-- After (stays in the SPA!) -->
<router-link to="/about">About</router-link>
```

Do this for all four links.

> **Why does this matter?** A regular `<a>` tag makes the browser fetch a whole new HTML page. `<router-link>` intercepts the click and swaps only the component, keeping state and skipping the reload.

> ✅ **Check:** Open DevTools → Network tab. Click between pages. You should see **no** new document requests.

---

### Step 4 (Bonus) — Custom active class (`router/index.js`)

Find `TODO 5`. Vue Router automatically adds `router-link-active` to the currently-active link, and our CSS already styles it. But you can rename that class to anything:

```js
const router = createRouter({
  history: createWebHistory(),
  routes,
  linkActiveClass: 'nav-active',   // ← add this line
})
```

Rename the CSS class in `main.css` too (`.router-link-active` → `.nav-active`) and confirm the active highlight still works.

---

### Step 5 — Make the Project cards clickable (`ProjectsView.vue`)

Open `src/views/ProjectsView.vue`. Find `TODO 7a`.

The project cards are `<div>` elements right now. Turn each one into a `<router-link>`:

```html
<!-- Before -->
<div class="card" v-for="project in projects" :key="project.id">

<!-- After -->
<router-link
  :to="`/projects/${project.id}`"
  class="card"
  v-for="project in projects"
  :key="project.id"
>
```

Don't forget to close with `</router-link>` instead of `</div>`.

---

### Step 6 — Read the URL param (`ProjectDetail.vue`)

This is the heart of the exercise. Open `src/views/ProjectDetail.vue`.

**TODO 7b:** Replace the `<a>` back-link with a `<router-link to="/projects">`.

**TODO 7c:** Uncomment and complete the three lines in `<script setup>`:

```js
const route     = useRoute()
const projectId = computed(() => Number(route.params.id))
const project   = computed(() => projects.find(p => p.id === projectId.value))
```

Then **delete** the three placeholder lines at the bottom of the script.

> **What's happening?** `useRoute()` returns a reactive object that always reflects the current URL. When you navigate to `/projects/2`, `route.params.id` becomes `"2"` (a string — don't forget `Number()` to convert it!). The `computed` re-runs automatically whenever the param changes.

> ✅ **Check:** Click each project card. Does the detail page update to show the right project?

---

### Step 7 — Build the 404 page (`NotFoundView.vue`)

Open `src/views/NotFoundView.vue`. The file has a commented-out starter template.

Uncomment it (remove the HTML comment wrappers) and make it work. The `.not-found` CSS is already waiting in `main.css`.

> ✅ **Check:** Visit `/anything-random` in the browser. Do you see your 404 page?

---

## Done? Try These Stretch Goals

- **Navigation guard:** In `router/index.js`, use `router.beforeEach()` to `console.log` the route name every time navigation happens.
- **Programmatic navigation:** Add a "Next Project →" button inside `ProjectDetail.vue` that calls `router.push()` to go to the next project ID.
- **Route meta:** Add a `meta: { title: 'Projects' }` field to each route and update `document.title` inside a `router.afterEach` guard.
- **Scroll behavior:** Add `scrollBehavior: () => ({ top: 0 })` to your `createRouter` config so the page always scrolls to the top on navigation.

---

## Cheat Sheet

```js
// Get current route info
import { useRoute } from 'vue-router'
const route = useRoute()
route.path        // '/projects/2'
route.params.id   // '2'
route.name        // 'ProjectDetail'
route.query       // { search: 'vue' }  ← from ?search=vue

// Navigate programmatically
import { useRouter } from 'vue-router'
const router = useRouter()
router.push('/projects')
router.push({ name: 'ProjectDetail', params: { id: 3 } })
router.back()
```

---

Good luck — you've got this! 🚀
