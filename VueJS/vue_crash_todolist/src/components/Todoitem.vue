<template>
  <div class="todo-item" v-bind:class="{'is_complete':todo.completed}">
    <p>
      <input
        type="checkbox"
        v-bind:checked="todo.completed"
        v-on:change="markComplete"
      >
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],
  methods: {
    markComplete() {
      this.$emit('toggle-complete', this.todo.id);
    }
  }
}
</script>

<style lang="css" scoped>
.todo-item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px #ccc dotted;
}

.is_complete {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>
