
  <template>
    <div class="not-found">
      <div class="page-title giant">404</div>
      <h2>Page Not Found</h2>
      <p>Hmm... <code>{{ route.path }}</code> doesn't exist.</p>
      <router-link to="/" class="btn">Go Home</router-link>
    </div>
  </template>

  <script setup>
  import { useRoute } from 'vue-router'
  const route = useRoute()
  </script>

