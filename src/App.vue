<template>
  <the-header title="RememberMe"></the-header>

  <base-card>
    <base-button @click="setVisibleComponent('resources-list')" :mode="visibleComponent === 'resources-list' ? '' : 'flat'">Resource list</base-button>
    <base-button @click="setVisibleComponent('add-resource')" :mode="visibleComponent === 'add-resource' ? '' : 'flat'">Add new resource</base-button>
  </base-card>



  <resources-list v-if="visibleComponent === 'resources-list'" :resources="resources"></resources-list>
  <keep-alive>
    <add-resource v-if="visibleComponent === 'add-resource'" @add-new-resource="addNewResource"></add-resource>
  </keep-alive>
</template>

<script>

  import ResourcesList from './components/ResourcesList.vue';
  import AddResource from './components/AddResource.vue';
  import TheHeader from './components/layouts/TheHeader.vue';

  export default {
    components: {
      ResourcesList,
      AddResource,
      TheHeader
    },

    data() {
      return {
        visibleComponent: 'resources-list',
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
    },
    methods: {

      addNewResource(title, description, link) {
        const newElement = {
          id: (this.resources[this.resources.length - 1].id) + 1,
          title: title,
          description: description,
          link: link
        };

        this.resources.push(newElement);
      },
      setVisibleComponent(elm) {
        this.visibleComponent = elm;
      }

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
