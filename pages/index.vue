<script setup lang="ts">
import { ChevronLeftIcon, ChevronRightIcon } from '@heroicons/vue/24/outline'

type Navigation = {
  label: string,
  to: string,
  isSelected: boolean
}

const corrousel = ref(0)

const profileCurrent = reactive({
  desc: "“I've tried countless cosmetics brands over the years, but none have delivered the flawless results I've experienced with Em cosmetics. From the silky textures to the vibrant colors, every product feels luxurious and delivers exceptional results. My skin has never looked better!”",
  by: 'Michael Williams',
  image: '/icons/profile/profile1.svg',
})

function nextProfile() {
  corrousel.value += 1

  if (corrousel.value === 1) {
    profileCurrent.desc = "“Em Cosmetics offers beautifully crafted makeup products that enhance natural beauty with innovative formulas and stunning packaging.”"
    profileCurrent.by = 'Anthony Stark'
    profileCurrent.image = 'https://as1.ftcdn.net/v2/jpg/01/97/11/64/1000_F_197116416_hpfTtXSoJMvMqU99n6hGP4xX0ejYa4M7.jpg'
  }

  if (corrousel.value === 2) {
    profileCurrent.desc = "“I think every guy fantasizes about being in the industry at some point. I just made it a reality. Also, He is not just a performer; he is become a meme and a cultural icon. Hence, I try to stay positive and keep pushing forward, no matter what.”"
    profileCurrent.by = 'Amanda Wonders'
    profileCurrent.image = 'https://as2.ftcdn.net/v2/jpg/02/18/93/97/1000_F_218939757_YqHgeD3BAANU87y2Kc10Y40HNVgDv5rK.jpg'
  }

  if (corrousel.value === 3) {
    profileCurrent.desc = "“Em Cosmetics delivers high-quality makeup with rich pigments and smooth application, perfect for achieving a flawless look every time.”"
    profileCurrent.by = 'Michael Williams'
    profileCurrent.image = '/icons/profile/profile1.svg'
    corrousel.value = 0
   }
}

function prevProfile() {
  if (corrousel.value === 0) {
    profileCurrent.desc = "“I think every guy fantasizes about being in the industry at some point. I just made it a reality. Also, He is not just a performer; he is become a meme and a cultural icon. Hence, I try to stay positive and keep pushing forward, no matter what.”"
    profileCurrent.by = 'Amanda Wonders'
    profileCurrent.image = 'https://as2.ftcdn.net/v2/jpg/02/18/93/97/1000_F_218939757_YqHgeD3BAANU87y2Kc10Y40HNVgDv5rK.jpg'
    corrousel.value = 3
  }

  if (corrousel.value === 1) {
      profileCurrent.desc = "“I've tried countless cosmetics brands over the years, but none have delivered the flawless results I've experienced with Em cosmetics. From the silky textures to the vibrant colors, every product feels luxurious and delivers exceptional results. My skin has never looked better!”"
      profileCurrent.by = 'Michael Williams'
      profileCurrent.image = '/icons/profile/profile1.svg'
      corrousel.value -= 1
      
  }

  if (corrousel.value === 2) {
    profileCurrent.desc = "“Em Cosmetics offers beautifully crafted makeup products that enhance natural beauty with innovative formulas and stunning packaging.”"
    profileCurrent.by = 'Anthony Stark'
    profileCurrent.image = 'https://as1.ftcdn.net/v2/jpg/01/97/11/64/1000_F_197116416_hpfTtXSoJMvMqU99n6hGP4xX0ejYa4M7.jpg'
    corrousel.value -= 1
  }

  if (corrousel.value === 3) {
    profileCurrent.desc = "“I think every guy fantasizes about being in the industry at some point. I just made it a reality. Also, He is not just a performer; he is become a meme and a cultural icon. Hence, I try to stay positive and keep pushing forward, no matter what.”"
    profileCurrent.by = 'Amanda Wonders'
    profileCurrent.image = 'https://as2.ftcdn.net/v2/jpg/02/18/93/97/1000_F_218939757_YqHgeD3BAANU87y2Kc10Y40HNVgDv5rK.jpg'
    corrousel.value -= 1
  }
}

const navs: Navigation[] = reactive([
  { label: 'home', to: '#home', isSelected: false },
  { label: 'about', to: '#about', isSelected: false },
  { label: 'shop', to: '#shop', isSelected: false },
  { label: 'products', to: '', isSelected: false },
  { label: 'contact', to: '', isSelected: false },
])

const headerImages = [
  '/illustrations/headerImage1.svg',
  '/illustrations/headerImage2.svg',
  '/illustrations/headerImage3.svg',
]

const shopImages = [
  { label: 'Skin care products', image: '/illustrations/shops/skin-products.svg' },
  { label: '"Organic" Cosmetics', image: '/illustrations/shops/organic-products.svg' },
  { label: 'Make-up products', image: '/illustrations/shops/makeup-products.svg' },
  { label: 'Soaps & Lotions', image: '/illustrations/shops/lotion-products.svg' },
]

function selectNav(nav: Navigation) {
  navs.forEach(nav => {
    nav.isSelected = false
  })
  nav.isSelected = true
}

function initializeNavigation() {
  navs[0].isSelected = true
}

initializeNavigation()
</script>

<style>
@font-face {
   font-family: myFirstFont;
   src: url(sansation_light.woff);
}
</style>

<template>
  <div class="w-full h-full relative overflow-x-hidden overflow-y-auto font-['Poppins']">
    <div class="w-full py-6 grid place-items-center border-b border-red-10" id="home">
      <div class="max-w-7xl w-full justify-between flex items-center">
        <img src="/icons/logo.svg" alt="Logo">

        <div class="flex items-center space-x-12">
          <a 
            v-for="nav in navs" 
            class="text-base outline-none capitalize font-semibold cursor-pointer"
            :class="[nav.isSelected ? 'text-red-10' : 'text-gray-0']"
            :href="nav.to"
            @click="selectNav(nav)"
          >{{ nav.label }}</a>
        </div>
      </div>
    </div>

    <div class="w-full py-16 grid place-items-center">
      <div class="max-w-7xl w-full flex flex-col items-start space-y-10">
        <div class="flex items-center space-x-6">
          <img v-for="image in headerImages" :src="image" alt="">
        </div>

        <div class="flex items-start justify-between w-full">
          <div class="flex flex-col items-start space-y-0 font-['Playfair_Display']">
            <p class="text-2xl text-gray-0">Glow beyond limits with</p>
            <p class="text-6xl font-semibold italic text-red-10">EM Cosmetics.</p>
          </div>

          <div class="flex flex-col items-start space-y-4">
            <p class="text-sm text-black w-80">
              Discover the glow within. Elevate your skincare routine with our nourishing essentials, designed to reveal your skin's natural brilliance
            </p>

            <button class="px-8 py-3 flex items-center space-x-4 justify-center bg-red-10">
              <span class="text-sm text-white">Discover</span>

              <svg width="24" height="12" viewBox="0 0 32 16" fill="none" xmlns="http://www.w3.org/2000/svg">
                <path d="M31.7071 8.70711C32.0976 8.31658 32.0976 7.68342 31.7071 7.29289L25.3431 0.928932C24.9526 0.538408 24.3195 0.538408 23.9289 0.928932C23.5384 1.31946 23.5384 1.95262 23.9289 2.34315L29.5858 8L23.9289 13.6569C23.5384 14.0474 23.5384 14.6805 23.9289 15.0711C24.3195 15.4616 24.9526 15.4616 25.3431 15.0711L31.7071 8.70711ZM0 9H31V7H0V9Z" fill="white"/>
              </svg>
            </button>
          </div>
        </div> 
      </div>
    </div>

    <div class="w-full relative my-40" id="about">
      <div class="left-0 bg-gray-5 flex items-center py-20 px-80 max-w-[1700px] relative overflow-hidden">
        <div class="flex flex-col items-start space-y-10">
          <p class="text-red-10 font-semibold italic text-4xl font-['Playfair_Display']">About</p>

          <p class="text-base text-black w-[520px]">
            <span class="font-semibold text-red-10">EM Cosmetics</span>
            stands as a beacon of transformative beauty, where each product embodies a fusion of cutting-edge innovation and timeless elegance, empowering individuals to express their unique identities with confidence and grace.
          </p>

          <button class="px-8 py-3 flex items-center space-x-4 justify-center border-2 border-red-10">
            <span class="text-base text-red-10">Learn More</span>
          </button>
        </div>

        <img src="/illustrations/aboutImage.svg" alt="About Image" class="absolute right-0" />
      </div>
    </div>

    <div class="w-full py-16 grid place-items-center" id="shop">
      <div class="max-w-7xl w-full flex flex-col items-start space-y-14">
        <p class="text-red-10 text-4xl font-semibold italic font-['Playfair_Display']">Shop by categories</p>

        <div class="flex items-center space-x-4">
          <div v-for="product in shopImages" class="relative overflow-hidden grid place-items-center">
            <img :src="product.image" alt="Products" class="z-0">
            <p class="text-sm text-white absolute z-10">{{ product.label }}</p>
          </div>
        </div>

        <div class="w-full flex flex-col items-center">
          <button class="px-8 py-3 flex items-center space-x-4 justify-center border-2 border-red-10">
            <span class="text-base text-red-10">Shop Now</span>
          </button>
        </div>
      </div>
    </div>

    <div class="w-full my-40 flex justify-end">
      <div class="bg-red-10 flex items-start relative overflow-hidden">
        <img src="/illustrations/peopleImage.svg" alt="About Image" class="left-0" />

        <div class="flex flex-col items-start space-y-28 w-[800px] px-12 py-16">
          <p class="text-white font-medium italic text-4xl font-['Playfair_Display']">What people say</p>

          <div class="w-full flex flex-col items-center space-y-10">
            <img src="/icons/comma.svg" alt="">

            <div class="flex items-center justify-between space-x-20">
              <button class="p-3 rounded-full bg-white" @click="prevProfile">
                <ChevronLeftIcon class="stroke-red-10 h-5 w-5" />
              </button>

              <p class="w-[450px] h-32 text-center text-base text-white">
                {{ profileCurrent.desc }}
              </p>

              <button class="p-3 rounded-full bg-white" @click="nextProfile">
                <ChevronRightIcon class="stroke-red-10 h-5 w-5" />
              </button>
            </div>

            <div class="space-y-10 flex flex-col items-center">
              <div class="space-y-6 flex flex-col items-center">
                <img :src="profileCurrent.image" class="w-12 h-12 rounded-full overflow-hidden object-cover" />

                <p class="text-white text-[15px] font-medium">{{ profileCurrent.by }}</p>
              </div>

              <div class="flex items-center space-x-3">
                <span 
                  class="w-2 h-2 bg-white rounded-full" 
                  :class="[corrousel === 0 ? '' : 'opacity-40']"
                />
                <span 
                  class="w-2 h-2 bg-white rounded-full"
                  :class="[corrousel === 1 ? '' : 'opacity-40']"
                />
                <span 
                  class="w-2 h-2 bg-white rounded-full" 
                  :class="[corrousel === 2 ? '' : 'opacity-40']"
                />
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="w-full pt-16 pb-52 grid place-items-center">
      <div class="max-w-7xl w-full flex flex-col items-center space-y-14">
        <img src="/illustrations/contact-image.svg" alt="Contact Image">

        <p class="text-center text-red-10 text-5xl font-semibold italic font-['Playfair_Display']">
          Be a Beauty Insider: <br />
          Sign Up for Membership
        </p>

        <div class="flex items-center space-x-4">
          <input 
            type="email"
            placeholder="Enter email address"
            class="px-4 py-3 w-72 border border-[#9A9A9A]"
          >

          <button class="px-12 py-3 flex items-center space-x-4 justify-center bg-red-10">
            <span class="text-base text-white">Subscribe</span>
          </button>
        </div>
      </div>
    </div>

    <div class="w-full py-12 grid place-items-center bg-black">
      <div class="max-w-7xl w-full flex items-center justify-between">
        <div class="flex flex-col items-start space-y-2">
          <img src="/icons/logo.svg" alt="Logo">
          <p class="text-base text-[#B1B1B1]">Copyright 2024 by Estella Mariz Escala</p>
        </div>

        <div class="flex flex-col items-start space-y-2 justify-end">
          <img src="/icons/logo.svg" alt="Logo" class="invisible">
          <p class="text-base text-[#B1B1B1]">Coded by John Vincent Miñoza</p>
        </div>
      </div>
    </div>
  </div>
</template>
