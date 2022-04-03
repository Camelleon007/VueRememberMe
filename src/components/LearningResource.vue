<template class="block">
  <li class="box">
    <base-card>
      <header>
        <h2 class="title">{{ title }}</h2>
      </header>

      <p>{{ description }}</p>
      <nav class="buttons is-right">
        <a class="button is-small is-info is-focused" :href="link"
          >View resource</a
        >
        <button class="button is-small is-danger is-focused">Delete</button>
      </nav>
    </base-card>
  </li>
</template>

<script>
export default {
  props: ['title', 'description', 'link'],
};
</script>
