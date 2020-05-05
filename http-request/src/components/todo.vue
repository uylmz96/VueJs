<template>
  <div class="row">
    <div class="col-md-8 offset-md-2 border d-flex justify-content-between flex-row align-items-center pt-2 pb-2">
      <span> {{todo.text}} </span>
      <button class="btn btn-danger" @click="$emit('deleteTodo',todo.id)">Sil</button>
    </div>
  </div>
</template>

<script>
export default {
    props:["todo"],
    mounted() {
        console.log("Mounted : todo => " +this.todo.id + " -> " + this.todo.text)
    },
}
</script>