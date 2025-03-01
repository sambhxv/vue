# vue-office

This template should help get you started developing with Vue 3 in Vite.

```
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
 *
```

