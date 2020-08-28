<template>
  <div class="bg-primary">
    <header class="w-full px-6">
      <Header />
      <div class="w-full mb-4 text-center border-t-2 border-b-2 border-l-0 border-r-0 border-black uppercase py-2">
        Memento Audere Semper
      </div>
    </header>
    <Nuxt />
    <footer class="w-full px-6">
      <div class="lg:flex">
        <div class="border border-black p-4 lg:w-1/5 text-center">
          <img src="/img/logo.png" alt="Julien Gabryelewicz" class="mx-auto" />
        </div>
        <div class="border border-black p-4 lg:w-4/5 lg:flex">
          <div class="p-4 lg:w-1/3">
            <p class="uppercase font-bold">Contact</p>
            <p>06 65 58 85 94</p>
            <p><a href="mailto:julien.gabryelewicz2@gmail.com" class="hover:underline">julien.gabryelewicz2@gmail.com</a></p>
          </div>
          <div class="p-4 lg:w-1/3">
            <p class="uppercase font-bold">Adresse</p>
            <p>4 avenue Léon Blum</p>
            <p>62510 Arques</p>
            <p>France</p>
          </div>
          <div class="p-4 lg:w-1/3">
            <p class="uppercase font-bold">Internet</p>
            <p><a href="https://github.com/juliengabryelewicz" target="_blank" class="hover:underline">Github</a></p>
          </div>
        </div>
      </div>
    </footer>
    <div class="text-center py-2">
      &copy; Julien Gabryelewicz - 2020 - <NuxtLink to="/page/mentions-legales" class="hover:underline">Mentions légales</NuxtLink>
    </div>
  </div>
</template>

<style>
.page-enter-active,
.page-leave-active,
.page-enter-active::before,
.page-enter-active::after,
.page-leave-active::before,
.page-leave-active::after {
  transition: transform 650ms cubic-bezier(.17,.67,.54,.98);
}
.page-enter-active::before,
.page-leave-active::before {
  content: '';
  position: fixed;
  top: 0;
  bottom: 0;
  width: 100%;
  height:100%;
  background: #e2e8f0;
  z-index: 1000;
}
.page-enter-active::before {
  left: -417px;
}
.page-leave-active::before {
  right: -417px;
}
.page-enter-active::after,
.page-leave-active::after {
  content: '';
  position: fixed;
  top: 0;
  bottom: 0;
  left: 0;
  right: 0;
  background-color: #e2e8f0;
  z-index:1000;
}
.page-leave::before {
  transform: translate3d(calc(-100% - 417px), 0, 0) scaleX(-1);
}
.page-leave-to::before {
  transform: scaleX(-1);
}
.page-leave::after {
  transform: translate3d(calc(-100% - 417px), 0, 0);
}
.page-enter-to::before,
.page-enter-to::after {
  transform: translate3d(calc(100% + 417px), 0, 0);
}
</style>
