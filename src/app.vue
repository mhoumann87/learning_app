<template>
  <the-header title="RememberMe"></the-header>
  <stored-resources :resources="storedResources"></stored-resources>
</template>

<script>
  import StoredResources from './components/learning-resources/StoredResources.vue';
  import TheHeader from './components/layouts/TheHeader.vue';

  export default {
    components: {
      StoredResources,
      TheHeader,
    },
    data() {
      return {
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
  };
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

  *,
  ::before,
  ::after {
    box-sizing: border-box;
  }

  html {
    font-family: 'Roboto', sans-serif;
  }

  body {
    margin: 0;
  }
</style>
