<template>
  <div class="w-full px-6">
    <div class="w-full mb-4 lg:flex">
      <div class="p-4 lg:w-1/2">
        <h2 class="font-bold font-title-article text-center text-2xl lg:text-4xl uppercase hover:underline"><NuxtLink :to="{ path: '/article/'+article.slug }">{{ article.title_home }}</NuxtLink></h2>
        <div>
          <img :src="article.img" :alt="article.alt" class="mx-auto w-48 lg:float-right" />
          {{ article.excerpt_home }}
          <div class="text-center p-4"><span class="border border-black p-2 hover:underline"><NuxtLink :to="{ path: '/article/'+article.slug }">En savoir plus</NuxtLink></span></div>
        </div>
      </div>
      <div class="p-4 lg:w-1/2">
        <ul>
          <li class="border border-black font-title-article uppercase text-center text-2xl md:text-3xl lg:text-4xl p-2 hover:underline"><NuxtLink :to="{ path: '/category/jeux-aventure'}">Jeux d'aventure</NuxtLink></li>
          <li class="border border-t-0 border-black font-title-article uppercase text-center text-2xl md:text-3xl lg:text-4xl p-2 hover:underline"><NuxtLink :to="{ path: '/category/linguistique'}">Linguistique</NuxtLink></li>
          <li class="border border-t-0 border-black font-title-article uppercase text-center text-2xl md:text-3xl lg:text-4xl p-2 hover:underline"><NuxtLink :to="{ path: '/category/litterature'}">Littérature</NuxtLink></li>
          <li class="border border-t-0 border-black font-title-article uppercase text-center text-2xl md:text-3xl lg:text-4xl p-2 hover:underline"><NuxtLink :to="{ path: '/category/programmation'}">Programmation</NuxtLink></li>
        </ul>
      </div>
    </div>
    <div class="w-full mb-4 lg:flex">
      <div class="bg-black border-r-2 border-black p-4 lg:w-1/2 text-white">
        <h2 class="font-bold font-title-article text-center text-2xl lg:text-4xl uppercase">Petite annonce</h2>
        <div>Actuellement en recherche d'emploi, je recherche un poste de développeur informatique (Node.js, PHP, Python...) dans la région Hauts-de-France, idéalement dans l'Audomarois, l'Artois ou la Côte d'Opale. Télétravail possible.</div>
        <div class="text-center p-4"><span class="border border-white p-2 hover:underline"><NuxtLink :to="{ path: '/page/cv'}">En savoir plus</NuxtLink></span></div>
      </div>
      <div class="p-4 lg:w-1/2">
        <h2 class="font-bold font-title-article text-center text-2xl lg:text-4xl uppercase">Le saviez-vous?</h2>
        <div><nuxt-content :document="saviezvous" /></div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content('articles', params.slug)
      .only(['alt', 'title_home', 'excerpt_home', 'img', 'slug'])
      .sortBy('position', 'desc')
      .limit(1)
      .fetch()

    const saviezvous = await $content('saviezvous', params.slug)
      .sortBy('position', 'desc')
      .limit(1)
      .fetch()
    return {
      'article' : articles[0],
      'saviezvous' : saviezvous[0],
    }
  },
  head() {
    return {
      title: "Julien Gabryelewicz - Développeur passionné par la linguistique",
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: "Julien Gabryelewicz - Développeur passionné par la linguistique"
        },
        {
          hid: 'keywords',
          name: 'keywords',
          content: "julien,gabryelewicz,développeur,recherche,emploi,linguistique,chatbot,php,python,node,deno"
        }
      ]
    }
  }
}
</script>
