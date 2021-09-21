<template>
  <div class="input-text">
    <input 
      type="text"
      @input="newTodo = $event.target.value" 
      placeholder="Введите текст..." 
      v-model="newTodo"
    />
    <btn 
      @click-handler="addText"
      text="Сохранить"
      :class="{'add-button': isAddButton}"
    />
    <ul
      :class="{todoList: isTodoList}">
      <todo-item
        v-for="(todo, index) in todoList" 
        :key="todo.id"
        :class="{done: todo.done}"
        :title="todo.title"
        @done="todo.done = !todo.done"
        @remove="todos.splice(index, 1); this.saveTodo()"
    >
      </todo-item>
    </ul>
  </div>
</template>

<script>
import Btn from '../Button/Btn.vue'
import TodoItem from '../TodoItem/TodoItem.vue'

export default {
  components: { Btn, TodoItem },
  name: 'InputText',
  data() {
    return {
      todos: [],
      newTodo: '',
      isDone: false,
      isTodoList: true,
      isAddButton: true
    }
  },
  methods: {
    addText() {
      if (!this.newTodo) {
        return
      }
      let title = this.newTodo
      let done = this.isDone
      let date = localStorage.getItem('date')
  
      let arr = {
        title, done, date
      }
      this.todos.push(arr)
      this.newTodo = ''
      this.saveTodo()
    },

    saveTodo() {
      const parsed = JSON.stringify(this.todos)
      localStorage.setItem('todos', parsed)
    }
  },
  mounted() {
    if (localStorage.getItem('todos')) {
      try {
        this.todos = JSON.parse(localStorage.getItem('todos'))
      } catch(e) {
        localStorage.removeItem('todos')
      }
    }
  },
  computed: {
    todoList() {
      return this.todos.filter(item => item.date === localStorage.getItem('date'))
    }
  }
}
</script>

<style scoped>

  .done {
    color:  rgba(124, 133, 216, 0.95);
    text-decoration-line: line-through;
  }

  .todoList {
    list-style-type: decimal;
    padding: 0 1rem;
    width: 95%;
    text-align: left;
  }

  .input-text {
    display: flex;
    flex-direction: column;
    align-items: baseline;
    padding: 1rem;
  }

  .input-text input {
    margin: 0 0 1rem;
    width: 90%;
    padding: .5rem 1rem;
    background: #F7F7F7;
    border: 1.5px solid rgba(181, 181, 181, 0.52);
    box-sizing: border-box;
    outline: none;
    border-radius: 3px;
  }

  ::placeholder {
    color: #9A8F8F;
    font-size: .7rem;
  }

  .input-text input:hover,
  .input-text input:focus {
    box-shadow: 0px 4px 4px rgba(190, 201, 205, 0.25);
  } 

  .add-button {
    filter: drop-shadow(0px 4px 4px rgba(202, 252, 255, 0.28));
    background: #BCC3FF;
    border: 1px solid #9AB6FF;
    box-sizing: border-box;
    border-radius: 3px;
    cursor: pointer;
  }

  .add-button:hover {
    background: #8995FF;
    transition: background .5s;
  }

</style>