<template>
  <div class="w-full mb-4 px-6"">
    <h1 class="text-center text-4xl lg:text-6xl font-bold uppercase font-title-article">{{ titlePage }}</h1>
    <div class="w-full lg:flex lg:flex-wrap">
      <div class="p-4 lg:w-1/2" v-for="article of articles">
        <img :src="article.img" :alt="article.alt" class="mx-auto w-48 lg:float-right" />
        <NuxtLink :to="{ path: '/article/'+article.slug }"><h2 class="font-bold uppercase hover:underline text-2xl md:text-3xl lg:text-4xl font-title-article">{{ article.title }}</h2></NuxtLink>
        <div>
          {{ article.date_creation }}
        </div>
        <div>
          {{ article.excerpt }}
        </div>
      </div>
    </div>
    <Pagination :page="page" :pageCount="pageCount" :slug="slug" />
  </div>
</template>

<script>

const pagination = {

  getTitleFromSlug(slug){
    switch (slug) {
      case 'experimentations':
        return "Expérimentations";
        break;
      case 'jeux-aventure':
        return "Jeux d'aventure";
        break;
      case 'linguistique':
        return "Linguistique";
        break;
      case 'litterature':
        return "Littérature";
        break;
      case 'programmation':
        return "Programmation";
        break
      default:
        return "";
        break;

    }
  },

  getArticlesFromPage($content, page, slug) {
    return $content('articles')
      .only(['title', 'date_creation', 'excerpt', 'img', 'alt', 'slug', 'type'])
      .where({ category: slug })
      .sortBy('position', 'desc')
      .skip(10 * (page - 1))
      .limit(10)
      .fetch()
  },

  async getNumberOfPages($content, slug) {
    return Math.ceil((await $content('articles').where({ category: slug }).only([]).fetch()).length / 10)
  },
}

export default {
  watchQuery: true,
  data() {
    return {
      page: 1,
    }
  },
  async asyncData({ $content, redirect, route, params }) {
    const slug = params.slug;
    const page = parseInt(route.query.page || '1') || 1;
    const titlePage = pagination.getTitleFromSlug(slug);
    if(titlePage === ""){
        redirect("/404");
    }

    const [articles, pageCount] = await Promise.all([
        pagination.getArticlesFromPage($content, page, slug),
        pagination.getNumberOfPages($content, slug),
    ])

    return {
      articles: articles, page: page, pageCount: pageCount, slug: slug, titlePage: titlePage
    }
  },
  head() {
    return {
      title: this.titlePage,
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.titlePage
        }
      ]
    }
  }
}
</script>