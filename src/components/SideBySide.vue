<template>
  <div>
    <h1 class="text-2xl">Vergleich</h1>
    <div class="grid divide-x divide-x-gray-400 grid-cols-1 md:grid-cols-2">
      <div class="px-2" v-for="(result, i) in [oldText, newText]" :key="i">
        <h2 class="text-lg font-medium">
          Stand {{ i === 0 ? "20.02.69" : "01.01.2022" }}
        </h2>
        <p class="text-justify">
          <span
            v-for="([type, text], i) in result"
            :key="i"
            :class="{
              'text-red-600': type === -1,
              'text-green-500': type === 1,
            }"
            v-text="text"
          />
        </p>
      </div>
    </div>
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
