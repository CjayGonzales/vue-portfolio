<template>
<b-list-group-item>
  <span v-if="todo.done" class="done">{{ todo.text }}</span>
  <span v-else>{{ todo.text }}</span>
  <span v-if="todo.done" class="float-end">&#128077;</span>
  <b-button v-else class="float-end" pill variant="outline-success" @click="completeTodo()">&#10003;</b-button>
  <b-button if class="float-end" pill variant="outline-success" @click="removeTodo()">&#128465;</b-button>

</b-list-group-item>
</template>
<script>
export default {
  name: "TodoItem",
  props: {
    todo: {
      type: Object,
      required: true
    }
  },
  methods: {
    completeTodo() {
      this.$emit("todo-completed", this.todo);
    },

    removeTodo(){
      this.$emit("remove-todo", this.todo);
    }
  }
}
</script>
<style>
.done {
  text-decoration: line-through;
}
</style>