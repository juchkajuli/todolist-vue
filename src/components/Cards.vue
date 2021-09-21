<template>
  <div class="cards">
    <input-date></input-date>
    <input-text></input-text>
  </div>
</template>

<script>
import InputText from './UI/Input/InputText.vue'
import InputDate from './UI/Input/InputDate.vue'

export default {
  name: 'Cards',
  components: {
    InputText,
    InputDate
  }
}
</script>

<style scoped>

.cards {
  background: rgba(251, 252, 244, 0.9);
  border: 1px solid #A4A0A0;
  box-sizing: border-box;
  box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
  border-radius: 2px;
  min-height: 200px;
  width: 300px;
}
</style>