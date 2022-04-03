<template>
  <ul>
    <LearningResource
      v-for="resource in storedResources"
      :key="resource.id"
      :title="resource.title"
      :description="resource.description"
      :link="resource.link"
    />
  </ul>
</template>

<script>
import LearningResource from './LearningResource.vue';
export default {
  components: {
    LearningResource: LearningResource,
  },
  inject: ['storedResources'],
};
</script>