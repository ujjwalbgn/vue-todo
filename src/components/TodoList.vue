<template>
  <div class="hello">
    <input type="text" v-model="newTodo" @keyup.enter="addTodo" class="todo-input" placeholder="what needs to be done">
    <div v-for="todo in todos" :key="todo.id" class="todo-item">
      <div>
        {{todo.title}}
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'todo-list',
    data () {
      return {
        newTodo : '',
        idForTodo : 3,
        todos: [
          {
          'id': 1,
          'title' : 'Finish Vue Screencast',
          'complete': false,
        },
          {
           'id' : 2,
           'title' : 'Take over the world',
           'complete' : false,
          }
          ]
      }
    },

    methods: {
      addTodo(){
        if(this.newTodo.trim().length == 0){
          return
        }
        this.todos.push({
          id: this.idForTodo,
          title: this.newTodo,
          completed : false,
        })

        this.newTodo = ''
        this.idForTodo++
      }
    }
  }
</script>

<style lang="scss">
  .todo-input {
    width: 100%;
    padding: 10px 18px;
    font-size: 18px;
    margin-bottom: 16px;

    &:focus{
      outline: 0;
    }

    .todo-item{
      margin-bottom: 12px;
      display: flex;
      align-items: center;
      justify-content: space-between;
    }
  }
</style>
