<template>
  <form @submit.prevent="newTodo(input)">
    <InputAT v-model="input" placeholder="Type and press ENTER" />
  </form>

  <TodoList :todos="filteredTodos" @click="toggleTodo" @delete="deleteTodo" />

  <div class="action-buttons">
    <ButtonAT @click="view = ''">All</ButtonAT>
    <ButtonAT @click="view = 'actives'">Actives</ButtonAT>
    <ButtonAT @click="view = 'done'">Dones</ButtonAT>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";

import useTodos from "@/modules/todos";

import InputAT from "@/components/InputAT.vue";
import ButtonAT from "@/components/ButtonAT.vue";
import TodoList from "@/components/TodoListAT.vue";

export default defineComponent({
  components: {
    InputAT,
    ButtonAT,
    TodoList,
  },
  setup() {
    const input = ref("");
    const { view, filteredTodos, newTodo, toggleTodo, deleteTodo } = useTodos();

    return { view, filteredTodos, newTodo, toggleTodo, deleteTodo, input };
  },
});
</script>

<style lang="scss" scoped>
.action-buttons {
  margin-top: 10px;

  & button {
    margin-right: 10px;
  }
}
</style>
