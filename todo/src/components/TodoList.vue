<template>
  <div class="py-5">
    <TransitionGroup name="fade-slide">
      <div v-for="todo in todos" :key="todo.id">
        <TodoItems v-if="value === ''" :todo="todo" @toggle-complete="$emit('toggle-complete',todo)"
          @delete-todo="$emit('delete-todo',todo)" />
        <TodoItems v-else-if="todo.completed === value" :todo="todo" @toggle-complete="$emit('toggle-complete',todo)"
          @delete-todo="$emit('delete-todo',todo)" />

      </div>
      <!--<TodoItems v-for="todo in todos" :key="todo.id" />-->
    </TransitionGroup>


  </div>
</template>

<script>
  import TodoItems from './TodoItems.vue'

  export default {
    props: ['todos', 'value'],
    components: {
      TodoItems
    },

  }
</script>

<style>
  .list-enter-active,
  .list-leave-active {
    transition: all 0.5s ease;
  }

  .list-enter-from,
  .list-leave-to {
    opacity: 0;
    transform: translateX(30px);
  }

  .fade-slide-enter-active,
  .fade-slide-leave-active {
    transition: all 400ms ease-out;
  }

  .fade-slide-enter-from {
    opacity: 0;
    transform: translateX(-100px)
  }

  .fade-slide-leave-to {
    opacity: 0;
    transform: translateX(100px)
  }
</style>