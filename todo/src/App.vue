<template>
<AddTodo @addTodo = "add" @sort="sortTodos"/>
  <div class="container">
    <TodoList :value= 'sort' :todos="todos" @toggle-complete ="complete" @delete-todo="deleteTodo"/>
  </div>
  <Transition name="fade">
  <ErrorModal v-if="errorModal" @close="errorModal=false" />
  </Transition>
</template>

<script>

import {v4 as uuidv4} from 'uuid'
import AddTodo from './components/AddTodo.vue'
import TodoList from './components/TodoList.vue'
import ErrorModal from './components/ErrorModal.vue'

export default {
  components:{
    AddTodo,
    TodoList,
    ErrorModal
 },
  data(){
    return{
      todos: [],

        sort:'',
        errorModal: false,
    
        
    }
  },
  methods:{
    sortTodos(val){
      switch(val){
        case 'false':
          this.sort = false
          break

          case 'true':
            this.sort = true
            break

            default:
              this.sort = ''
      }
    },
    add(title){
      const todo = {
        id: uuidv4(),
        title,
        completed: false

      }
      this.todos.push(todo)
    },
    complete(todo){
      todo.completed = !todo.completed
    },
    deleteTodo(_todo){
      if(!_todo.completed){
        this.errorModal= true

        return
      }
      this.todos = this.todos.filter(todo => todo.id !== _todo.id)
      this.errorModal = false
    }
  }
    
}
</script>

<style>
.fade-enter-active,
.fade-leave-active {
  transition: opacity 500ms ease;
}

.fade-enter-from,
.fade-leave-to {
  opacity: 0;
}

</style>