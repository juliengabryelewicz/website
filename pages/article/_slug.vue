<template>
  <div class="w-full flex flex-wrap px-6 py-12 lg:flex-row-reverse md:flex-row-reverse">
    <Menu :toc="article.toc" />
    <article class="lg:w-4/5 lg:px-6 leading-normal">
      <div class="relative xs:px-8 lg:px-16 xs:w-full markdown-body post-right">
        <h1 class="font-bold font-title-article text-4xl lg:text-6xl uppercase">{{ article.title }}</h1>
        <p class="pb-4">{{ article.date_creation }}</p>
        <div class="article-content">
          <nuxt-content :document="article" />
        </div>
      </div>
    </article>
  </div>
</template>
<script>
export default {
  async asyncData({ $content, params, redirect }) {
    try{
      const article = await $content('articles', params.slug).fetch()
      return {
        article: article
      }
    } catch (e) {
      redirect("/404");
    }
  },
  head() {
    return {
      title: this.article.seo_title,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.article.seo_description
        },
        {
          hid: 'keywords',
          name: 'keywords',
          content: this.article.seo_keyword
        }
      ]
    }
  }
}
</script>