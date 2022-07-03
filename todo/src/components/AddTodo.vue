<template>
  <form @submit.prevent="addTodo" class="bg-white border-bottom py-5">
    <div class="container">
      <div class="row">
        <div class="col-8">
          <div class="input-group mb-3 shadow bg-body rounded">
            <input type="text" class="form-control " placeholder="Add todo.." v-model="title" ref ="focusInput">
            <button @click="addTodo" class="btn btn-danger" type="button">Add</button>
          </div>
        </div>
        <div class="col-4">
          <select class="form-select shadow bg-body rounded" v-model="select" @change="$emit('sort',select)">
            <option value="">Show all</option>
            <option value="false">Show Uncompleted</option>
            <option value="true">Show Completed</option>
          </select>
        </div>
      </div>
      <small v-if="error"  class="text-danger">{{ error }} </small>
    </div>
  </form>
</template>

<script>
  export default {
    data(){
      return{
        title: '',
        select: '',
        error: ''
      }
    },
    methods:{
      addTodo(){
        if(this.title.trim() === ''){
          this.error = 'You need to enter what todo'
          this.$refs.focusInput.focus()
          return
         }
         this.error = ''
         this.$emit('addTodo',this.title)
         this.title=''
         this.$refs.focusInput.focus()
      }
    }
}
</script>

<style>

</style>