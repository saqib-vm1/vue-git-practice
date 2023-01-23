<template>
    <h1>Provider Component A - {{ count }}</h1>
    <ProvideInjectB />
</template>

<script setup>
    import { provide, ref, readonly } from 'vue';
    import ProvideInjectB from './ProvideInjectB.vue'

    let count = ref(0);
    function updateCount() {
        count.value++
    }
    provide('count', readonly(count));
    provide('updateCount', updateCount)
</script>