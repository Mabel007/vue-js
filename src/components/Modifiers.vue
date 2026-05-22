<template>
<!-- using $event special variable -->
<button @click="warn('Form cannot be submitted yet.', $event)">
  Submit
</button>

<!-- using inline arrow function -->
<button @click="(event) => warn('Form cannot be submitted yet.', event)">
  Submit
</button>
<button @click="greet" class="bg-green-500">Greet</button>
   
<button v-on:click="doThis" class="bg-blue-500 text-white">Click me</button>
<button v-on:[dynamic]="doThis">Dynamic</button>
<button v-on:click="doThat('hello', $event)"></button>
<!--The shorthand of v-on is @ -->
<button @click="doThis"></button>
<button @click.stop="doThis"></button>
<button @click.prevent="doThis"></button>
<form @submit.prevent></form>

<!--Using v-on(@) on a button, with an argument(click),a modifier(.stop.prevent), and a value(="doThis") -->
<button @click.stop.prevent="doThis"></button>

<input @keyup.enter="onEnter" />
<!-- Alt + Enter -->
<input @keyup.alt.enter="clear" />

<!-- Ctrl + Click -->
<div @click.ctrl="doSomething">Do something</div>

<button v-on:click.once="doThis"></button>

<button v-on="{ mousedown: doThis, mouseup: doThat }"></button>

<MyComponent @my-event="handleThis" />

<!-- inline statement -->
<MyComponent @my-event="handleThis(123, $event)" />




</template>

<script setup>
function doThis(){
    console.log("the button was clicked!");
}
 const dynamic = 'click'

 const name = ref('Vue.js');

 function greet(event){
    alert(`Hello ${name.value}!`)
 }

 if(event){
    alert(event.target.tagName)
 }

 function warn(message, event) {
  // now we have access to the native event
  if (event) {
    event.preventDefault()
  }
  alert(message)
}
</script>