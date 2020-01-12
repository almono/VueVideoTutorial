<template>
  <div>
    <input v-model="search" @keyup.enter="onInput" />
    <button class="btn btn-danger" @click="onInput">Search</button>
  </div>
</template>


<script>
export default {
  data: function() {
    return {
      search: ''
    }
  },
  name: 'SearchBar',
  methods: {
    onInput: function() {
      this.$emit('termChange', this.search);
    }
  }
};
</script>


<style scoped>
  input {
    width: 75%;
  }
  div {
    text-align: center;
    margin: 20px;
  }
</style>
