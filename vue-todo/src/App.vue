<template>
  <button @click="toggleForm">Toggle Form</button>
  <p>{{ displayForm ? "Form is displayed" : "Form is not displayed" }}</p>
  <div>
    <!--
        v-if completely removes the element from the DOM if the condition is false
        but v-show only toggles the display property of the element
      -->
    <form v-show="displayForm" @submit.prevent="createTodo">
      Description
      <input v-model="data.todo" type="text" id="todo-description" />
      <!--
        v-model provides a two-way binding with a reactive variable, so when the input changes, it updates the reactive value.
        or if the value changes it updates the input field
      -->
      <input type="submit" value="Create" />
    </form>
    <ol>
      <li v-for="(todo, index) in data.todos">
        <del v-if="todo.completed"> {{ todo.description }} </del>
        <span v-else> {{ todo.description }} </span>
        <button @click="deleteTodo(index)">Delete</button>
        <button v-if="!todo.completed" @click="markAsCompleted(index)">
          Done
        </button>
      </li>
    </ol>
  </div>
</template>

<script setup>  // composition API, but options API can also be used, core difference being, the second one divides the script into methods and data objects
import { reactive, ref } from "vue";  // ref creates a reactive value as well, it can be updated using name.value

const displayForm = ref(false);

const data = reactive({
  todos: [],
  todo: "",
});

function createTodo() {
  if (!data.todo) return;
  data.todos.push({
    description: data.todo,
    completed: false,
  });
  data.todo = "";
}

function markAsCompleted(index) {
  data.todos[index].completed = true;
}

function deleteTodo(index) {
  data.todos.splice(index, 1);
}

function toggleForm() {
  displayForm.value = !displayForm.value;
}
</script>
