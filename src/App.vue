<template>
  <h3>Created and imported Vue component.</h3>
  <TemplateSyntax />
  <hr />
  <hr />
  <VModel />
  <hr />
  <hr />
  <ProvideInject />
  <hr />
  <hr />
  <WatchersComponent />
  <hr />
  <hr />
  <TemplateRefs />
</template>

<script setup>
  import TemplateSyntax from './components/template-syntax/TemplateSyntax.vue';
  import VModel from './components/v-model/VModel.vue';
  import ProvideInject from './components/provide-inject/ProvideInject.vue';
  import WatchersComponent from './components/watchers/WatchersComponent.vue'
  import TemplateRefs from './components/template-refs/TemplateRefs.vue';
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
