<template>
  <div>
    <input @input="onInput" type="text" />
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

<style lang="scss" scoped></style>
