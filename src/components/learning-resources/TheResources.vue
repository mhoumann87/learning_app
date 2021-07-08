<template>
  <base-card>
    <base-button @click="setSelectedTab('stored-resources')"
      >Stored Recources</base-button
    >
    <base-button @click="setSelectedTab('add-resources')"
      >Add Resources</base-button
    >
  </base-card>
  <component :is="selectedTab"></component>
</template>

<script>
  import StoredResources from './StoredResources.vue';
  import AddResources from './AddResource.vue';

  export default {
    components: {
      StoredResources,
      AddResources,
    },
    data() {
      return {
        selectedTab: 'stored-resources',
        storedResources: [
          {
            id: 'vuejs',
            title: 'Official Guide',
            descriptopn: 'The official Vue documentation.',
            link: 'https://www.vuejs.org',
          },
          {
            id: 'google',
            title: 'Google',
            descriptopn:
              'Learning to use Google is inportand for every developer',
            link: 'https://google.com',
          },
        ],
      };
    },
    provide() {
      return {
        resources: this.storedResources,
      };
    },
    methods: {
      setSelectedTab(tab) {
        this.selectedTab = tab;
      },
    },
  };
</script>
