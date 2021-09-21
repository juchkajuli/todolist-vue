<template>
  <div class="headline">
    <h2>{{title}}</h2>
  </div>
</template>

<script>
export default {
  name: 'Headline',
  data() {
    return {
      title: 'Список дел'
    }
  }
}
</script>

<style scoped>
  .headline {
    box-sizing: border-box;
    margin: 1rem 0;
    text-align: left;
    padding: 0 1rem;
    display: flex;
    align-items: center;
    justify-content: space-between;
    background: rgba(251, 252, 244, 0.9);
    border: 1px solid #A4A0A0;
    box-shadow: 0px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 3px;
    width: 300px;
  }

  .headline h2 {
    margin: 1rem 0;
  }
  
</style>