<template>
  <div>
    <h1 class="text-2xl">Zusammenfassung</h1>
    <p class="text-justified">
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
export default {
  name: "Unified",
  props: ["result"],
};
</script>
