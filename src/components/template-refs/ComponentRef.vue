<template>
    <p>This is {{ childComponent }}</p>
</template>

<script setup>
    import { ref, defineExpose } from 'vue';

    const childComponent = ref('child Component');
    defineExpose({
        childComponent
    })
</script>