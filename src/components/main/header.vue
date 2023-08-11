<template>
  <header
    class="header h-[86px] duration-300"
    :class="{ 'bg-black/50 backdrop-filter backdrop-blur-md': y }"
  >
    <div
      class="flex items-center lg:justify-start justify-between w-full text-white mx-auto"
      :class="{ 'text-neutral-600': y }"
    >
      <a href="/">
        <img
          class="lg:mr-[64px] mr-auto"
          src="/images/logo.svg"
          alt="logo"
        >
      </a>

      <button
        class="lg:hidden w-11 h-11 text-primary z-120"
        @click="toggleMenu"
      >
        <i class="text-2xl mdi mdi-menu" />
      </button>
      <div class="<lg:hidden flex items-center text-primary">
        <a
          v-for="link in headerLinks"
          :key="link.title"
          :href="link.href"
          class="font-light mr-[46px]"
        >
          {{ link.title }}
        </a>
      </div>
    </div>
  </header>

  <transition>
    <div
      v-if="showMenu"
      class="lg:hidden flex flex-center flex-col fixed top-0 left-0 right-0 bottom-0 bg-black/80 text-primary font-light z-110"
      @click="toggleMenu"
    >
      <a
        v-for="link in headerLinks"
        :key="link.title"
        :href="link.href"
        class="mb-10"
      >
        {{ link.title }}
      </a>
    </div>
  </transition>
</template>

<script setup lang="ts">
import { ref } from 'vue'
import { useWindowScroll } from '@vueuse/core'
import headerLinks from '@/assets/json/header.json'

const { y } = useWindowScroll()
const showMenu = ref(false)

const toggleMenu = () => {
  showMenu.value = !showMenu.value
  if (showMenu.value) {
    document.getElementsByTagName('html')[0].classList.add('html--use-modal')
  } else {
    document.getElementsByTagName('html')[0].classList.remove('html--use-modal')
  }
}
</script>
