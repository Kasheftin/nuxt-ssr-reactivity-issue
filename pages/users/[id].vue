<template>
  <div>
    <div>
      User #{{id}}:
    </div>
    <div>
      {{ data }}
    </div>
  </div>
</template>

<script setup lang="ts">
import { breadcrumbs } from '@/stores/breadcrumbs'

const route = useRoute()
const id = computed(() => route.params.id)

const { data, refresh } = useAsyncData<{id: number; title: string}>('user', async () => {
  const result = await fetch(`https://gorest.co.in/public/v2/users/${id.value}`)
  return await result.json()
})

watch(id, refresh)

watch(() => [id.value, data.value?.id], () => {
  breadcrumbs.value = ['users', data.value?.title || '#' + id.value]
}, { immediate: true })

</script>
