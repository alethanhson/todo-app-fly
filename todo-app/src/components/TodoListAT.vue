<template>
  <div v-for="todo in todos" :key="todo.id" class="todos">
    <Checkbox
      v-model="todo.done"
      type="checkbox"
      class="todo-checkbox"
      @click="$emit('click', todo)"
    />

    <div :class="{ 'todo-done': todo.done }" class="todo-text">
      {{ todo.text }}
    </div>

    <ButtonAT @click="$emit('delete', todo)">Delete</ButtonAT>
  </div>
</template>

<script lang="ts">
import { defineComponent } from "vue";
import Checkbox from "@/components/CheckboxAT.vue";
import ButtonAT from "@/components/ButtonAT.vue";

export default defineComponent({
  props: {
    todos: Array,
  },
  emits: ["click", "delete"],
  components: {
    Checkbox,
    ButtonAT,
  },
});
</script>

<style lang="scss" scoped>
.todos {
  font-size: 18px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 600;
  padding: 20px;
  margin: 10px 0;
  transition: var(--transition);
  border-radius: var(--borderRadius);
  background-color: var(--bg-secondary);
  border: 1px solid #ddd;

  .todo-checkbox {
    margin-right: 20px;
  }

  .todo-text {
    color: var(--color-secondary);
    width: 100%;
  }

  .todo-done {
    text-decoration: line-through;
  }
}
</style>
