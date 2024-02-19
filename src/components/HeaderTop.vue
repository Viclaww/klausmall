<script setup lang="js">
import { RouterLink as Link } from 'vue-router'
console.log('Hello')
const navLinks = [
  { name: 'Hamper Collection', path: '/hamper-collections' },
  { name: 'Grocery Shopping', path: '/groceries' },
  { name: 'Contact Us', path: '/contact-us' },
  { name: 'About Us', path: '/about' }
]
</script>

<template>
  <div>
    <img src="../assets/KlausMall.svg" />
    <div class="">
      <Link v-for="link in navLinks" :key="link.name" :to="link.path">{{ link.name }}</Link>
    </div>
  </div>
</template>

<style scoped></style>
