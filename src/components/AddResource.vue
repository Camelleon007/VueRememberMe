<template>
  <base-dialog
    v-if="inputIsInvalid"
    title="Invalid Input"
    @close="confirmError"
  >
    <template #default>
      <p>Unfortunatlly something went wrong.</p>
      <p>Please look into it</p>
    </template>
    <template #actions>
      <button @click="confirmError">Okey</button>
    </template>
  </base-dialog>
  <base-card>
    <form id="default" @submit.prevent="submitData">
      <div>
        <label class="label" for="title">Title</label>
        <input
          class="input"
          id="title"
          name="title"
          type="text"
          ref="titleInput"
        />
      </div>
      <div>
        <label class="label" for="desc">Desc</label>
        <textarea
          class="textarea"
          id="desc"
          name="desc"
          type="text"
          rows="3"
          ref="descInput"
        />
      </div>
      <div>
        <label class="label" for="link">Link</label>
        <input class="input" id="link" name="link" type="url" ref="linkInput" />
      </div>
      <div>
        <button
          type="submit"
          from="default"
          class="button is-small is-info is-focused p-1 m-1"
        >
          Add Resource
        </button>
      </div>
    </form>
  </base-card>
</template>

<script>
export default {
  inject: ['addResource'],
  data() {
    return {
      inputIsInvalid: false,
    };
  },
  methods: {
    confirmError() {
      this.inputIsInvalid = false;
    },
    submitData() {
      const enteredTitle = this.$refs.titleInput.value;
      const enteredDesc = this.$refs.descInput.value;
      const enteredUrl = this.$refs.linkInput.value;

      if (
        enteredTitle.trim() === '' ||
        enteredDesc.trim() === '' ||
        enteredUrl.trim() === ''
      ) {
        this.inputIsInvalid = true;
        return;
      }

      this.addResource(enteredTitle, enteredDesc, enteredUrl);
    },
  },
};
</script>