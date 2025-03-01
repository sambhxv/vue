<template>
  <div :class="['px-2 py-1 text-xs font-semibold flex w-fit p-2 rounded-2xl', colorToClasses[color]]">
    <slot/> <!-- slot gets replaced by the value passed in by the parent -->
    <!-- {{ props.status }} -->
  </div>
</template>

<script setup>
import { computed, useSlots } from "vue";

const statusToColor = {
  Active: "green",
  Inactive: "red",
  Paid: "green",
  Unpaid: "orange",
  Pending: "yellow",
};

const colorToClasses = {
  green: "text-green-700 bg-green-300",
  red: "text-red-700 bg-red-300",
  orange: "text-amber-700 bg-amber-300",
  yellow: "text-yellow-700 bg-yellow-300",
};

const props = defineProps({
  status: String,
});

const slots = useSlots();

const color = computed(() => {
    let children = slots.default()[0].children.trim();
    console.log(children)
    return statusToColor[children];
    // return statusToColor[props.status]
});
</script>
