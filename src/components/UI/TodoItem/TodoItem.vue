<template>
  <li class="li-todo">
    {{title}}
    <div class="btn-list">
      <button 
        :class="{'btn-done': isBtnDone}"
        @click="$emit('done')"
      >
      </button>
      <button 
        @click="$emit('remove')"
        :class="{'btn-remove': isBtnRemove}"
      >
      </button>
    </div>
  </li>
</template>

<script>
export default {
  name: 'TodoItem',
  props: {
    title: String
  },
  data() {
    return {
      isBtnDone: true,
      isBtnRemove: true
    }
  }
}
</script>

<style scoped>
  .btn-done, 
  .btn-remove {
    border: none;
    cursor: pointer;
  }

 .btn-done {
    background: url('../../../assets/done.png') no-repeat;
    background-size: 20px;
    width: 28px;
    height: 22px;
    margin-right: .5rem;
  }

  .btn-done:hover,
  .btn-remove:hover {
    opacity: .5;
    transition: opacity .5s;
  }

  .btn-remove {
    background: url('../../../assets/remove.png') no-repeat;
    width: 18px;
    height: 22px;
    background-size: 12px;
  }

  .li-todo {
    position: relative;
    overflow-wrap: break-word;
    width: 75%;
  }

  .btn-list {
    position: absolute;
    display: inline-block;
    right: -35%;
    top: 0px;
  }
</style>