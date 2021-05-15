<template>
  <p>
    <span
      v-for="([type, text], i) in result"
      :key="i"
      :class="{ 'text-red-500': type === -1, 'text-green-500': type === 1 }"
      v-text="text"
    />
  </p>
</template>

<script>
export default {
  name: "Unified",
  props: ["result"],
};
</script>
