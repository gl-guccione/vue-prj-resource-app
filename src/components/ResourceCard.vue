<template>
  <li>
    <base-card>
      <header>
        <h3>{{ resource.title }}</h3>
        <base-button @click="$emit('delete-resource', resource.id)" mode="flat">Delete</base-button>
      </header>
      <p>{{ resource.description }}</p>
      <nav>
        <a :href="resource.link">{{ resource.link }}</a>
      </nav>
    </base-card>
  </li>
</template>

<script>
  export default {
    props: ['resource'],
    emits: ['delete-resource']
  };
</script>

<style scoped>
  li {
    margin: auto;
    max-width: 40rem;
  }

  header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  h3 {
    font-size: 1.25rem;
    margin: 0.5rem 0;
  }

  p {
    margin: 0.5rem 0;
  }

  a {
    text-decoration: none;
    color: #ce5c00;
  }

  a:hover,
  a:active {
    color: #c89300;
  }
</style>
