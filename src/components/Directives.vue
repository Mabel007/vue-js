<template>
    <span v-text="msg"></span>
    <span>{{msg}}</span>
    <div v-html="html"></div>
    <h1 v-show="ok">Show me!</h1>
    <div v-if="type === 'A'" class="text-blue-700 font-bold">

        A
    </div>
    <div v-else-if="type === 'B'" class="text-red-700 font-extrabold">
        B
    </div>
    <div v-else-if="type === 'C'" class="text-purple-700 font-extrabold">
        C
    </div>
    <div v-else class="text-yellow-700 font-extrabold">
        Not A/B/C
    </div>
    <div :id class="bg-blue-500"></div>

    <div v-for="(bucket, index) in buckets"></div>
    <div v-for="(value, key) in object"></div>
    <div v-for="(value, name, index) in object"></div>

    <div v-for="bucket in buckets">
        {{ bucket.text }}
        {{ bucket.id }}
    </div>

    <li v-for="item, index in items">
        {{ index }} - {{ item.name }}
    </li>

    <li v-for="detail in details">
        {{ detail.message  }}
    </li>
    <li v-for="(test, index) in tests">
  {{ parentMessage }} - {{ index }} - {{ test.message }}
</li>
    <ul>
  <li v-for="value in myObject">
    {{ value }}
  </li>
</ul>

    

</template>

<script setup>

import { ref, reactive } from 'vue';
   const type = "D";
   const msg = "Using Interpolation in Vue";
   const id = 5;
   const html=`<div>This is a valid <span style='color:red'>html</span></div>`;
   const ok = false;

   const details = ref(
    [
        {
            message: 'Foo'
        },
        {
            message: 'Bar'
        }
    ]
   );

   const parentMessage = ref('Parent')
   const tests = ref([{
    message: 'New' 
   }, { message: 'Car'}])

   const items = ref([
    {
        name: "Naj",
        role: "Developer"
    },
    {
        name: "Faith",
        role: "Student"
    }
   ]);

   const buckets = [
    {
        text: 'something',
        id: 'randomId'
    }
   ];
   const myObject = reactive({
    title: 'How to do lists in Vue',
    author: 'Jane Doe',
    publishedAt: '2016-04-10'
    });
    const object = {
        id: 'unique-id',
        class: 'counter-button'
    }

   

</script>