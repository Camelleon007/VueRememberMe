<template>
  <base-card class="buttons">
    <button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      class="button is-small is-info is-focused p-1 m-1"
    >
      Stored resources
    </button>
    <button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      class="button is-small is-primary is-focused p-1 m-1"
    >
      Add resource
    </button>
  </base-card>
  <keep-alive>
    <component :is="selectedTab"></component>
  </keep-alive>
</template>

<script>
import StoredResources from './StoredResources.vue';
import AddResource from './AddResource.vue';

export default {
  components: {
    StoredResources,
    AddResource,
  },
  data() {
    return {
      selectedTab: 'stored-resources',
      resources: [
        {
          id: 'official-guile',
          title: 'Official Guide',
          description: 'The official Vue.js documentation.',
          link: 'https://vuejs.org',
        },
        {
          id: 'google',
          title: 'Google',
          description: 'You kneed to know Google.',
          link: 'https://google.pl',
        },
      ],
    };
  },
  provide() {
    return {
      storedResources: this.resources,
      addResource: this.addResource,
    };
  },
  computed: {
    storedResButtonMode() {
      return this.selectedTab === 'stored-resources' ? null : 'flat';
    },
    addResButtonMode() {
      return this.selectedTab === 'add-resource' ? null : 'flat';
    },
  },
  methods: {
    setSelectedTab(tab) {
      this.selectedTab = tab;
    },
    addResource(title, description, url) {
      console.log('addResource START');
      const newResource = {
        id: new Date().toISOString(),
        title: title,
        description: description,
        link: url,
      };
      this.resources.unshift(newResource);
      this.selectedTab = 'stored-resources';
    },
  },
};
</script>