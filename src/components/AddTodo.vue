<template>
  <div class="addTodo">
    <input
      placeholder="Listeye Ekle..."
      type="text"
      name="add"
      id="add"
      v-model="addTodo"
      @keypress.enter="$emit('addTodo', addTodo)"
    />
  </div>
</template>
<script>
export default {};
</script>
<style scoped>
.addTodo {
  text-align: center;
}
input {
  border-radius: 12px;
  border: 1px solid lightgrey;
  outline: none;
  padding: 5px;
}
</style>
