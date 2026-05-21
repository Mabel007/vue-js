<template>
    <p>My name is {{ name }}</p>
</template>

<script setup>
import { ref } from 'vue';

const name = ref("Naj");

</script>