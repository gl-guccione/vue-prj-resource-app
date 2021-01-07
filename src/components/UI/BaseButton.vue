<template>

  <button :class="mode">
    <slot></slot>
  </button>

</template>

<script>
export default {

  props: ['mode']

}
</script>

<style scoped>

  button {
    padding: 0.75rem 1.5rem;
    font-family: inherit;
    background-color: #24049b;
    border: 1px solid #24049b;
    color: white;
    cursor: pointer;
    border-radius: 10px;
  }

  button:hover,
  button:active {
    background-color: #150061;
    border-color: #150061;
  }

  .flat {
    background-color: transparent;
    color: #3a0061;
    border: none;
  }

  .flat:hover,
  .flat:active {
    background-color: #edd2ff;
  }

</style>