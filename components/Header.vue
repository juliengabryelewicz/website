<template>
    <div class="w-full lg:flex">
      <div class="p-4 lg:w-1/3">
        <div id="menuArea">
          <input :checked="checked" type="checkbox" id="menuToggle" class="hidden"></input>

          <label for="menuToggle" class="menuOpen" @click="toggleMenu(true)">
            <div class="open" @click="toggleMenu(true)"></div>
          </label>

          <div class="menu menuEffects">
            <label for="menuToggle" @click="toggleMenu(false)"></label>
            <div class="menuContent">
              <ul>
                <li @click="toggleMenu(false)"><NuxtLink :to="{ path: '/category/jeux-aventure'}">Jeux d'aventure</NuxtLink></li>
                <li @click="toggleMenu(false)"><NuxtLink :to="{ path: '/category/linguistique'}">Linguistique</NuxtLink></li>
                <li @click="toggleMenu(false)"><NuxtLink :to="{ path: '/category/litterature'}">Littérature</NuxtLink></li>
                <li @click="toggleMenu(false)"><NuxtLink :to="{ path: '/category/programmation'}">Programmation</NuxtLink></li>
              </ul>
            </div>
          </div>
        </div>
      </div>
      <div class="p-4 lg:w-1/3 text-center block text-secondary w-full font-bold text-center no-underline font-title uppercase text-2xl sm:text-2xl md:text-4xl lg:text-4xl text-primary"><NuxtLink :to="{ path: '/'}">Julien Gabryelewicz</NuxtLink></div>
      <div class="p-4 lg:w-1/3 text-right hidden lg:block"></div>
    </div>
</template>
<script>
export default {
  data () 
  {
    return{
      checked: false
    }
  },
  methods:{
    toggleMenu (newChecked) {
      this.checked = newChecked;
    } 
  }
}
</script>