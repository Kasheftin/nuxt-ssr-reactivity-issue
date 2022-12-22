<template>
  <div>
    <div>Users:</div>
    <div v-for="user in data" :key="user.id">
      <nuxt-link :to="`/users/${user.id}`">
        {{ user.name }}
      </nuxt-link>
    </div>
  </div>
</template>

<script setup lang="ts">
const { data } = useAsyncData('users', async () => {
  const result = await fetch('https://gorest.co.in/public/v2/users')
  return await result.json()
})
</script>
