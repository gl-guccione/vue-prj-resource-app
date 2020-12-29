<template>
  <the-header title="RememberMe"></the-header>

  <resources-list :resources="resources"></resources-list>
</template>

<script>

  import ResourcesList from './components/ResourcesList.vue';
  import TheHeader from './components/layouts/TheHeader.vue';

  export default {
    components: {
      ResourcesList,
      TheHeader
    },

    data() {
      return {
        resources: [
          {
            id: 1,
            title: 'Official Guide',
            description: 'The official Vue.js documentation.',
            link: 'https://vuejs.org'
          },
          {
            id: 2,
            title: 'google',
            description: 'Google website.',
            link: 'https://www.google.com'
          }
        ]
      };
    }
  };

</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

  * {
    box-sizing: border-box;
  }

  html {
    font-family: 'Roboto', sans-serif;
  }

  body {
    margin: 0;
  }
</style>
