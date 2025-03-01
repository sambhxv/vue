# vue-todo

```
<script setup> // composition API instead of options API, options work directly in the markup, requires build tools setup for transpiling
  import {reactive} from "vue";

  const data = reactive({
    count: 0
  })

  const increment = () => {
    data.count++
  }
</script>
```
