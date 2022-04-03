<template>
  <div @click="$emit('close')" class="modal-background"></div>
  <dialog open>
    <header class="modal-card-title">
      <slot name="header">
        <h2>{{ title }}</h2>
      </slot>
    </header>
    <section>
      <div class="modal-content">
        <slot></slot>
      </div>
    </section>
    <menu>
      <slot name="actions">
        <button @click="$emit('close')">Close</button>
      </slot>
    </menu>
  </dialog>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: false,
    },
  },
  emits: ['close'],
};
</script>

<style scoped>
dialog {
  z-index: 100;
}
.modal-background {
  z-index: 99;
}
</style>