<template>

  <base-card>

    <base-alert v-if="errorVisibile">
      <span>
        Compila tutti i campi
      </span>
      <button @click="errorVisibile = false">chiudi</button>
    </base-alert>

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
      },
      errorVisibile: false
    };
  },
  methods: {
    addNewResourceInComponent() {
      if (this.newResource.insertedTitle != '' && this.newResource.insertedDescription != '' && this.newResource.insertedLink != '') {
        this.$emit('add-new-resource', this.newResource);
        this.newResource.insertedTitle = '';
        this.newResource.insertedDescription = '';
        this.newResource.insertedLink = '';
      } else {
        this.errorVisibile = true;
      }
    },
  }

}
</script>

<style scoped>

</style>