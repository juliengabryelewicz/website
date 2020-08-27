<template>
  <nav class="lg:w-1/5 lg:px-6 leading-normal">
    <ul class="list-decimal">
      <li v-for="link of toc" v-if="link.depth === 2" :key="link.id">
        <NuxtLink :to="`#${link.id}`" class="hover:underline py-2">{{ link.text }}</NuxtLink>
      </li>
    </ul>
  </nav>
</template>

<script>
export default {
  props: {
    toc: {
      required: true
    }
  }
}
</script>