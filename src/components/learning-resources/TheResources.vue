<template>
  <base-card>
    <base-button
      @click="setSelectedTab('stored-resources')"
      :mode="storedResButtonMode"
      >Stored Recources</base-button
    >
    <base-button
      @click="setSelectedTab('add-resource')"
      :mode="addResButtonMode"
      >Add Resources</base-button
    >
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
        storedResources: [
          {
            id: 'vuejs',
            title: 'Official Guide',
            description: 'The official Vue documentation.',
            link: 'https://www.vuejs.org',
          },
          {
            id: 'google',
            title: 'Google',
            description:
              'Learning to use Google is inportand for every developer',
            link: 'https://google.com',
          },
        ],
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
    provide() {
      return {
        resources: this.storedResources,
        addRecousce: this.addRecousce,
        deleteResource: this.deleteResource,
      };
    },
    methods: {
      setSelectedTab(tab) {
        this.selectedTab = tab;
      },
      addRecousce(title, description, link) {
        const newResource = {
          id: new Date().toISOString(),
          title,
          description,
          link,
        };
        // console.log(newResource);
        this.storedResources.unshift(newResource);
        this.selectedTab = 'stored-resources';
      },
      deleteResource(resId) {
        const resIndex = this.storedResources.findIndex(
          res => res.id === resId
        );
        this.storedResources.splice(resIndex, 1);
      },
    },
  };
</script>
