<template class="container">
  <ul>
    <the-header title="My Title"></the-header>
  </ul>
  <the-resources></the-resources>
</template>

<script>
import TheHeader from './components/layouts/TheHeader.vue';
import TheResources from './components/TheResource.vue';
export default {
  components: {
    TheHeader,
    TheResources,
  },
};
</script>

<style>
</style>