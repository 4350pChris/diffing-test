<template>
  <div class="grid divide-x divide-x-gray-400 grid-cols-1 md:grid-cols-2">
    <p class="px-2" v-for="(result, i) in [oldText, newText]" :key="i">
      <span
        v-for="([type, text], i) in result"
        :key="i"
        :class="{ 'text-red-500': type === -1, 'text-green-500': type === 1 }"
        v-text="text"
      />
    </p>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  name: "Unified",
  props: ["result"],
  setup(props) {
    const oldText = computed(() => props.result.filter(([type]) => type < 1));
    const newText = computed(() => props.result.filter(([type]) => type > -1));
    return { newText, oldText };
  },
};
</script>
