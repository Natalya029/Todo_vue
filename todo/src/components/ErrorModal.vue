<template>



<div class="modal-bg" @click.self="$emit('close')">
  <div class="card shadow error-modal bg-secondary">
<div class="card-header">
  <h4 class="text">Ooops!</h4>
</div>
<div class="card-body">
  <p>You need to complite the todo</p>
  <button class="btn btn-danger btn-sm" @click="$emit('close')" >ok</button>
</div>
  </div>
</div>



</template>

<script>
export default {
  name: 'errorModal'

}
</script>

<style>

.modal-bg{
  position: absolute;
  inset: 0;
  z-index: 10;
  color:aliceblue
}
.error-modal{
  max-width: 400px;
  margin: 15rem auto;
}




</style>