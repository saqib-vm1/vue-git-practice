<template>
    <h1>Slots</h1>
    <p>
        Whatever we pass between component's opening and closing tags,
        that is said slot content in vue.
            We can pass string, html content and even other components as
        slot content.
            In the child component we use <code>&lt;slot&gt;</code> element
        to indicate where the parent-provided slit content should be rendered.
    </p>
    <ChildSlotComponent>
        <p><em>This is slot content from parent.</em></p>
    </ChildSlotComponent>
    <p>--------------- NAMED SLOTS -----------------</p>
    <NamedSlot>
        <template v-slot:header>
            <h3>Header slot content</h3>
        </template>
        <p>This will implicitly become part of default slot.</p>
        <template #footer>
            <h4>Footer slot content</h4>
        </template>
    </NamedSlot>
</template>

<script setup>
    import ChildSlotComponent from './ChildSlotComponent.vue';
    import NamedSlot from './NamedSlot.vue';
</script>