<template>
    <h1>Text Interpolation</h1>
    <h4>The most basic form of data binding is text interpolation using the "Mustache" syntax (double curly braces):</h4>
    <p>Reactive message with text interpolation : {{ reactiveMsg }}</p>
</template>

<script setup>
import { ref } from 'vue';
    // the 'ref()' function provides the reactive data.
    let reactiveMsg = ref('Reactive Message');
</script>