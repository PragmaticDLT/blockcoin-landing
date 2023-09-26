<template>
  <section class="bg-about bg-normal px-4 py-12 md:py-16 lg:py-24">
    <div class="container mx-auto">
      <div class="text-primary text-2xl sm:text-4xl text-center">
        The BlockCoin Team
      </div>
      <div
        class="mt-16 flex items-center justify-center md:flex-row flex-col gap-6"
      >
        <div
          v-for="member in team"
          :key="member.name"
          class="h-full"
        >
          <div class="bg-[#0D0B0BB0] border border-primary rounded-lg text-center px-3 py-6">
            <img
              class="mx-auto"
              :src="member.avatar"
              width="152"
              height="152"
              :alt="member.name"
            >
            <div class="text-primary font-bold text-2xl md:text-4xl mt-6">
              {{ member.name }}
            </div>
            <div class="text-primary font-bold md:text-xl mt-2">
              {{ member.role }}
            </div>
            <div class="mt-6">
              <p
                v-for="(paragraph, pIdx) in member.shortDescription.split('\n')"
                :key="pIdx"
              >
                {{ paragraph }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue'
import { useWindowSize } from '@vueuse/core'
import { Swiper, SwiperSlide } from 'swiper/vue'
import team from '@/assets/json/team.json'

const { width } = useWindowSize()
const slideCount = computed(() => width.value > 1024 ? 3 : width.value / 400)
</script>
