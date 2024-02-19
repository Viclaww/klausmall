<script setup>
import { ref } from 'vue'
import { RouterLink as Link } from 'vue-router'

const isOpen = ref(false)
console.log(isOpen.value)
const navLinks = [
  { name: 'Hamper Collection', path: '/hamper-collections' },
  { name: 'Grocery Shopping', path: '/groceries' },
  { name: 'Contact Us', path: '/contact-us' },
  { name: 'About Us', path: '/about' }
]
</script>

<template>
  <div class="flex mt-5 items-center px-4 md:px-6 justify-between md:justify-evenly">
    <div class="flex items-center">
      <img
        v-if="!isOpen"
        @click="isOpen = !isOpen"
        class="w-8 h-8 mt-5 mr-3 md:hidden"
        src="../assets/menu-svgrepo-com.svg"
        alt=""
      />
      <Link to="">
        <img class="h-10 relative z-30 md:z-0 cursor-pointer" src="../assets/KlausMall.svg" />
      </Link>
    </div>

    <span
      v-if="isOpen"
      @click="isOpen = !isOpen"
      class="text-xl absolute z-40 cursor-pointer font-extrabold right-5 top-10S"
    >
      <img src="../assets/cancel.png" alt="" />
    </span>
    <!-- md:flex w-[50%] hidden justify-between -->
    <div
      :class="[
        isOpen ? 'w-full' : 'w-0 md:w-[50%]  pointer-events-none md:pointer-events-auto',
        'absolute pt-[25%] left-0 top-0 border-r border-ash-shade flex flex-col md:border-0 transition-all duration-400 z-10 h-[100vh] md:flex-row md:justify-between md:relative md:pt-0 md:h-auto md:w-full bg-white'
      ]"
    >
      <Link
        v-for="link in navLinks"
        :class="[
          isOpen
            ? 'translate-y-0 opacity-100'
            : 'translate-y-3 w-full text-nowrap opacity-0 md:opacity-100',
          'font-medium transition-all duration-300 hover:text-red-primary py-6 md:py-0 pl-5 text-lg border-b md:border-0 md:text-lg border-ash-shade/40'
        ]"
        class=""
        :key="link.name"
        :to="link.path"
        >{{ link.name }}</Link
      >
    </div>
    <div class="flex items-center justify-around w-[30%] md:w-[10%]">
      <div
        class="w-10 box-border cursor-pointer h-10 p-2 bg-white shadow-black rounded-sm shadow-sm"
      >
        <img src="../assets/Profile_Icon_UIA.png" alt="person" />
      </div>

      <img class="w-12 h-12 cursor-pointer" src="../assets/Cart.png" alt="person" />
    </div>
  </div>
</template>

<style scoped></style>
