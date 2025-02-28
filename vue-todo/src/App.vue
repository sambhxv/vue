<template>
  <h1>Hello!</h1>
  <p>{{ data.count }}</p>
  <button @click="increment">Increment</button>
</template>

<script setup> // composition API instead of options API, options work directly in the markup, requires build tools setup for transpiling
  import {reactive} from "vue";

  const data = reactive({
    count: 0
  })

  const increment = () => {
    data.count++
  }
</script>
