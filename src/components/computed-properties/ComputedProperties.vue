<template>
    <h1>Computed Properties Component</h1>
    <div>Computed Property: {{ sumOfNumbers }}</div>

    <button @click="change_count">Increment Count: {{ count }}</button>
</template>

<script setup>
    import { ref, computed, onUpdated } from 'vue';

    const count = ref(0);
    const n = ref(50);

    const sumOfNumbers = computed(() => {
        console.log('computed function')
        let sum = 0;
        for(let i=1; i<=n.value; i++) {
            sum += i;
        }
        return sum
    });

    function change_count() {
        count.value++;
        if(count.value % 10 === 0) {
            n.value = count.value;
        }  
    }

    onUpdated(() => {
        console.log('component updated');
    })
    // Notice in the console that component re-renders on every count incement...
    // but computed function executes its callback only when its dependencies has changed.
</script>

<!-- computed function runs its callback only when its dependencies are changed -->
<!-- if its dependencies didn't on changed it returns the cached value based on its dependencies on component re-renders-->