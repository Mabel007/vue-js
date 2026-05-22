<template>
  <div class="m-3 bg-blue-700 text-white">
    <p>Has published books:</p>
    <span>{{ publishedBooksMessage }}</span>
    <p class="mt-3 bg-red-700 text-black font-extrabold">{{ totalBooks }}</p>
    <p class="mt-3 bg-purple-700 text-black font-extrabold">{{ availableBooks }}</p>
    <p class="mt-3 bg-yellow-700 text-white font-extrabold">{{ totalPages }}</p>
    <p class="mt-3 bg-green-700 text-white font-extrabold">{{ expensiveBooks }}</p>
    <p class="mt-3 bg-blue-700 text-white font-extrabold">{{ latestBook }}</p>
    <p class="mt-3 bg-red-700 text-white font-extrabold">{{ hasManyFollowers }}</p>
    <p class="mt-3 bg-yellow-700 text-white font-extrabold">{{ fullInfo }}</p>
    <p class="mt-3 bg-purple-700 text-white font-extrabold">{{ hasGithub }}</p>
    
  </div>

</template>

<script setup>
import { computed, reactive } from 'vue';

const author = reactive({
  name: 'John Doe',
  age: 34,
  country: 'Canada',
  isMarried: true,
  followers: 12500,
  rating: 4.8,

  books: [
    {
      id: 1,
      title: 'Vue 2 - Advanced Guide',
      pages: 320,
      published: 2021,
      isAvailable: true,
      price: 25,
      category: 'Advanced'
    },
    {
      id: 2,
      title: 'Vue 3 - Basic Guide',
      pages: 180,
      published: 2023,
      isAvailable: false,
      price: 18,
      category: 'Beginner'
    },
    {
      id: 3,
      title: 'Vue 4 - The Mystery',
      pages: 450,
      published: 2025,
      isAvailable: true,
      price: 35,
      category: 'Intermediate'
    }

  ],
  socialLinks: {
    twitter: '@johndoe',
    github: 'johndoe-dev',
    website: 'https://johndoe.dev'
  },
  hobbies: ['Coding', 'Reading', 'Gaming'],

  address: {
    city: 'Toronto',
    zipCode: 'M5V 3L9'
  }



});

// a computed ref{}
const publishedBooksMessage = computed(() => {
  return author.books.length > 0 ? 'Yes' : 'No'
});

const totalBooks = computed(() => {
  return author.books.length;
});
const availableBooks = computed(() => {
  return author.books.filter(book => book.isAvailable)
})

const totalPages = computed(() => {
  return author.books.reduce((total, book) => total + book.pages, 0)
})
const expensiveBooks = computed(() => {
  return author.books.filter(book => book.price > 20)
})

const latestBook = computed(() => {
  return [...author.books].sort((a, b) => b.published - a.published)[0]
})

const hasManyFollowers = computed(() => {
  return author.followers > 10000
})

const fullInfo = computed(() => {
  return `${author.name} from ${author.address.city}`
})
const hasGithub = computed(() => {
  return `${author.socialLinks.github}`
})


</script>