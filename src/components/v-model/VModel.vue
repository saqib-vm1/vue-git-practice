<template>
    <h1>v-model binding</h1>
    <input v-model="firstName" />
    <CustomInput v-model="lastName" />
    <VModelArguments v-model:age="age" v-model:address="address" />
    <ModelModifiers v-model:title.upperCase="title" />
    <p>{{ firstName }} - {{ lastName }} - {{ age }} - {{ address }} - upper cased : {{ title }}</p>
</template>

<script setup>
    import { ref } from 'vue';
    import CustomInput from './CustomInput.vue';
    import VModelArguments from './VModelArguments.vue';
    import ModelModifiers from './ModelModifiers.vue';

    const firstName = ref('default');
    const lastName = ref('');
    const age = ref('');
    const address = ref('');
    const title = ref('');
</script>