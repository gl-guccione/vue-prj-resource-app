<template>

  <base-card>

    <base-alert v-if="errorVisibile">
      <span>
        Compila tutti i campi
      </span>
      <button @click="errorVisibile = false">chiudi</button>
    </base-alert>

    <form @submit.prevent="addNewResourceInComponent">

      <div class="form-control">
        <label for="title">Title</label>
        <input id="title" name="title" type="text" placeholder="insert title" v-model="newResource.insertedTitle">
      </div>
      <div class="form-control">
        <label for="description">Description</label>
        <textarea id="description" name="description" cols="30" rows="3" placeholder="insert description" v-model="newResource.insertedDescription"></textarea>
      </div>
      <div class="form-control">
        <label for="link">Link</label>
        <input id="link" name="link" type="text" placeholder="insert link" v-model="newResource.insertedLink">
      </div>

      <base-button type="submit">Add resource</base-button>

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
  label {
    font-weight: bold;
    display: block;
    margin-bottom: 0.5rem;
  }

  input,
  textarea {
    display: block;
    width: 100%;
    font: inherit;
    padding: 0.15rem;
    border: 1px solid #ccc;
  }

  input:focus,
  textarea:focus {
    outline: none;
    border-color: #3a0061;
    background-color: #f7ebff;
  }

  .form-control {
    margin: 1rem 0;
  }
</style>