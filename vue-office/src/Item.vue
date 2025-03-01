<template>
  <li>
    <h2>{{ props.first_name }} {{ props.last_name }}</h2>
    <img :src="props.image" alt="" />
  </li>
</template>

<script setup>
const props = defineProps({
  first_name: String,
  last_name: String,
  image: String,
});
</script>
