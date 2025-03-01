<template>
  <div v-if="data">
    <ul>
      <li v-for="item in data">
        {{ item.first_name }} {{ item.last_name }}
        <img :src="item.avatar" alt="" />
      </li>
    </ul>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";
import Item from "./Item.vue";
/**
 * difference bw reactive and ref:
 * let loading = ref(false);
 * loading.value = true; ------------> updates the value
 *
 * let loading = reactive({ value: false });
 * loading.value = true; ------------> does not update the value
 * but
 * data.loading = true; ------------> updates the value
 *
 * We use reactive when we have a reactive object, but for single values, ref is preferred.
 */

const data = ref(null);
const OFFICE_API = "https://reqres.in/api/users";

onMounted(() => { // executes when the component of App.vue is mounted
  fetch(OFFICE_API)
    .then((d) => d.json())
    .then((message) => {
      console.log(message.data);
      data.value = message.data;
    });
});
</script>
