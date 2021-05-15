<template>
  <div>
    <h1 class="text-2xl my-2">Zusammenfassung</h1>
    <p class="text-justified">
      <span
        v-for="([type, text], i) in result"
        :key="i"
        :class="{
          'bg-red-100 text-red-800': type === -1,
          'bg-green-50 text-green-800': type === 1,
        }"
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
