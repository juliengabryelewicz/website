<template>
  <div class="w-full flex flex-wrap px-6 py-12 lg:flex-row-reverse md:flex-row-reverse">
  <Menu :toc="page.toc" />
  <article class="lg:w-4/5 lg:px-6 leading-normal">
    <div class="relative xs:px-8 lg:px-16 xs:w-full markdown-body post-right">
      <h1 class="font-bold font-title-article text-4xl lg:text-6xl uppercase">{{ page.title }}</h1>
      <div class="article-content">
      <nuxt-content :document="page" />
      </div>
    </div>
  </article>
  </div>
</template>
<script>
export default {
  async asyncData({ $content, params, redirect }) {
    try{
      const page = await $content('pages', params.slug).fetch()
        return {
            page: page
        }
    } catch (e) {
      redirect("/404");
    }
  },
  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('fr', options)
    }
  },
  head() {
    return {
      title: this.page.seo_title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.page.seo_description
        },
        {
          hid: 'keywords',
          name: 'keywords',
          content: this.page.seo_keyword
        }
      ]
    }
  }
}
</script>