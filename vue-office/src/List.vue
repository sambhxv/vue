<template>
  <div v-if="data">
    <ul>
      <Item
        v-for="item in data"
        :first_name="item.first_name"
        :last_name="item.last_name"
        :image="item.avatar"
      />
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted, watch } from "vue";
import Item from "./Item.vue";

const data = ref(null);
watch(data, (newData) => {  // watch for changes in data
  console.log(newData);
});

const OFFICE_API = "https://reqres.in/api/users";

// executes when the component of App.vue is mounted
onMounted(() => {
  fetch(OFFICE_API)
    .then((d) => d.json())
    .then((message) => {
      console.log(message.data);
      data.value = message.data;
    });
});
</script>
