<template>
  <div>
    <MarkdownRenderer :value="data" />
  </div>
</template>

<script setup>
const { content } = useRoute().query
const { data } = await useAsyncData(content, async () => {
  return await $fetch('/api/parse', {
    method: 'POST',
    cors: true,
    body: {
      id: 'content:index.md',
      content
    }
  })
})
</script>
