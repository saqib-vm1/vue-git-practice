<template>
    <h1>Template Refs</h1>
    <p>When we need direct access to the DOM elements we make use of refs.</p>
    <input ref="firstName" />
    <!-- ============================================= -->
    <p>------------- Function Refs -----------------</p>
    <p>
        Instead of a string key, the ref attribute can also be bound to a function.
        The function receives the element reference as the first argument. 
    </p>
    <input name="functionRef" :ref="(el) => { functionRef = el }" />
    <!-- ============================================== -->
    <p>------------ Ref on Component ----------------</p>
    <p>
        ref can also be used on a child component. In this case the reference 
        will be that of a component instance:
    </p>
    <ComponentRef ref="componentRef" />
</template>

<script setup>
    import { onMounted, ref } from 'vue';
    import ComponentRef from './ComponentRef.vue';
    // To obtain the reference, we need to declare a ref with the same name:
    const firstName = ref(null);
    const functionRef = ref(null);
    const componentRef = ref(null);

    onMounted(() => {
        firstName.value.focus();
        console.log(functionRef.value);

        // In order to access the child component properties,
        // those must be exposed from the child component.
        console.dir(componentRef.value.childComponent)
    })
</script>