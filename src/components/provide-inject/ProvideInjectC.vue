<template>
    <h1>Consumer Component C</h1>
    <p>{{ count }}</p>
    <button @click="updateCount">UpdateCount</button>
</template>

<script setup>
    import { inject } from 'vue';

    let count = inject('count');
    let updateCount = inject('updateCount');
</script>