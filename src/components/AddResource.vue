<template>

  <base-card>

    <form @submit.prevent="addNewResourceInComponent">

      <div>
        <input type="text" placeholder="insert title" v-model="newResource.insertedTitle">
      </div>
      <div>
        <textarea cols="30" rows="10" placeholder="insert description" v-model="newResource.insertedDescription"></textarea>
      </div>
      <div>
        <input type="text" placeholder="insert link" v-model="newResource.insertedLink">
      </div>

      <base-button>Add resource</base-button>

    </form>

  </base-card>

</template>

<script>
export default {

  emits: ['add-new-resource'],
  data() {
    return {
      newResource: {
        insertedTitle: '',
        insertedDescription: '',
        insertedLink: '',
      }
    };
  },
  methods: {
    addNewResourceInComponent() {
      if (this.newResource.insertedTitle != '' && this.newResource.insertedDescription != '' && this.newResource.insertedLink != '') {
        this.$emit('add-new-resource', this.newResource);
        this.newResource.insertedTitle = '';
        this.newResource.insertedDescription = '';
        this.newResource.insertedLink = '';
      }
    }
  }

}
</script>

<style scoped>

</style>