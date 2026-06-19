<template>
  <div id="layout">
    <header class="site-header">
      <div class="header-inner">
        <span class="logo">Ream Folio</span>

        <nav class="main-nav">
          <a href="/">Home</a>
          <a href="/about">About</a>
          <a href="/projects">Projects</a>
        </nav>
      </div>
    </header>

    <main class="page-content">
      <router-view v-slot="{ Component }">
        <transition name="fade" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>

    <footer class="site-footer">
      <p>Vue Router Exercise — built by Mr, ReamKhorn<strong>at PNC</strong> 🚀</p>
    </footer>
  </div>
</template>

<script setup>
</script>
