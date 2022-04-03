<template>
  <header>
    <h1 class="title is-1 has-text-centered has-text-white">{{ title }}</h1>
  </header>
</template>

<script>
export default {
  props: ['title'],
};
</script>

<style scoped>
header {
  width: 100%;
  height: 5rem;
  background-color: #640032;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
