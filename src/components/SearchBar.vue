<template>
  <div>
    <input @input="onInput" type="text" placeholder="Search video" />
  </div>
</template>

<script>
export default {
  name: 'SearchBar',
  methods: {
    onInput(e) {
      //   console.log(e.target.value)
      this.$emit('termChange', e.target.value)
    }
  }
}
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
