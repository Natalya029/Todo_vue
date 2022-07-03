<template>
<div class="bg-white d-flex justify-content-between align-items-center p-2 mb-3 rounded shadow">
<p class="m-0 h5" :class="{ done: todo.completed }" @click="$emit('toggle-complete')" >{{todo.title}}</p>
<button class="btn btn-danger btn-sm" @click="$emit('delete-todo')" >X</button>
</div>
  
</template>

<script>
    export default {
        props: ['todo'],
         methods:{
           
        }
    }
</script>
        
       

<style scoped>
p{
    color:rgb(74, 182, 182);
    cursor: pointer;
    user-select: none;
}
.done{
    text-decoration: line-through;
    color: rgb(219, 210, 198);
}
</style>