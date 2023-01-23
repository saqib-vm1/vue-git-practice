<template>
    <input :value="age" @input="$emit('update:age', $event.target.value)" />
    <input :value="address" @input="$emit('update:address', $event.target.value)" />
</template>

<script setup>
    import { defineProps, defineEmits } from 'vue';

    defineProps(['age', 'address']);
    defineEmits(['update:age', 'update:address']);

</script>