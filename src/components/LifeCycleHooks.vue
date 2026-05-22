<template>
  <div class="p-5">
    <h1 class="text-2xl font-bold mb-4">Vue Lifecycle Hooks</h1>

    <button
      id="count"
      class="bg-green-700 text-white px-4 py-2 rounded"
      @click="count++"
    >
      Count: {{ count }}
    </button>
  </div>
</template>

<script setup>
import {
  ref,
  onBeforeMount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeUnmount,
  onUnmounted
} from 'vue'

const count = ref(0)

console.log('1. setup() executed')
console.log('Initial count:', count.value)

/*
|--------------------------------------------------------------------------
| BEFORE MOUNT
|--------------------------------------------------------------------------
| Component has been initialized
| Template is compiled
| DOM elements are NOT yet available
*/

onBeforeMount(() => {
  console.log('2. onBeforeMount')
  console.log('DOM is not mounted yet')
})

/*
|--------------------------------------------------------------------------
| MOUNTED
|--------------------------------------------------------------------------
| Component is now visible on the page
| DOM elements can now be accessed
*/

onMounted(() => {
  console.log('3. onMounted')
  console.log('Component has been mounted')

  const button = document.getElementById('count')
  console.log('Button text:', button.textContent)
})

/*
|--------------------------------------------------------------------------
| BEFORE UPDATE
|--------------------------------------------------------------------------
| State has changed
| DOM has NOT updated yet
*/

onBeforeUpdate(() => {
  console.log('4. onBeforeUpdate')
  console.log('Old DOM value:', document.getElementById('count').textContent)
  console.log('New count value:', count.value)
})

/*
|--------------------------------------------------------------------------
| UPDATED
|--------------------------------------------------------------------------
| DOM has now updated with latest changes
*/

onUpdated(() => {
  console.log('5. onUpdated')
  console.log('Updated DOM value:', document.getElementById('count').textContent)
})

/*
|--------------------------------------------------------------------------
| BEFORE UNMOUNT
|--------------------------------------------------------------------------
| Component is about to be removed
*/

onBeforeUnmount(() => {
  console.log('6. onBeforeUnmount')
  console.log('Component will be removed soon')
})

/*
|--------------------------------------------------------------------------
| UNMOUNTED
|--------------------------------------------------------------------------
| Component has been fully removed
*/

onUnmounted(() => {
  console.log('7. onUnmounted')
  console.log('Component has been removed from the DOM')
})
</script>