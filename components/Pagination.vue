<template>
    <ul v-if="pageCount > 1" class="flex list-reset border border-black rounded">
      <li v-for="num in pageCount" v-if="num != null" class="block text-secondary border-r border-black px-3 py-2">
        <NuxtLink v-if="num != page" :to="{ path: '/category/'+slug, query: { page: num } }">{{ num }}</NuxtLink>
        <span v-else>{{ num }}</span>
      </li>
    </ul>
</template>

<script>
export default {
  props: {
    page: {
      type: Number,
      required: true
    },
    pageCount: {
      type: Number,
      required: true
    },
    slug: {
      type: String,
      required: true
    }
  }
}
</script>