<template>
    <button @click="$emit('clickHandler')">{{text}}</button>
</template>

<script>
export default {
  name: 'Btn',
  props: {
    text: String
  }
}
</script>

<style scoped>

button {
  padding: .5rem 1.2rem;
  cursor: pointer;
}
</style>