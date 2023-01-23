<template>
    <div>
        <label>v-model with modifier</label>
        <input :value="title" @input="modifyTitle" />
    </div>

</template>

<script setup>
    import { defineProps, defineEmits } from 'vue';

    const props = defineProps(['title', 'titleModifiers']);
    const emit = defineEmits(['update:title']);

    console.log(props.title, props.titleModifiers, 'rr')
    
    function modifyTitle(e) {
        let value = e.target.value;
        if(props.titleModifiers.upperCase) {
            value = value.toUpperCase();
        }

        emit('update:title', value);
    }

</script>