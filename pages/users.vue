<template>
  <div>
    <div>
      <nuxt-link to="/">
        Home
      </nuxt-link>
    </div>
    <div>
      Navbar: {{ breadcrumbs.join(' > ') }}
    </div>
    <nuxt-page />
  </div>
</template>

<script setup lang="ts">
import { breadcrumbs } from '@/stores/breadcrumbs'

</script>
