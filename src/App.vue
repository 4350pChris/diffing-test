<template>
  <section>
    <button
      class="shadow text-sm uppercase p-2 my-4 rounded transition bg-gray-100 hover:bg-gray-300 hover:shadow focus:outline-none"
      @click="unified = !unified"
    >
      {{ unified ? "nebeneinander" : "zusammengefasst" }} ansehen
    </button>
    <UnifiedView v-if="unified" :result="result" />
    <SideBySide v-else :result="result" />
  </section>
  <section class="cursor-pointer" @click="code = !code" title="collapse">
    <h1 class="text-2xl leading-6 mt-8 mb-4">Code</h1>
    <div>
      <template v-if="code">
        <code class="block" v-for="token in result" :key="token.toString()">
          {{ token }}
        </code>
      </template>
    </div>
  </section>
</template>

<script>
import Diff from "text-diff";
import text from "./assets/text.json";
import { ref } from "vue";
import UnifiedView from "./components/Unified.vue";
import SideBySide from "./components/SideBySide.vue";

export default {
  name: "App",
  components: { UnifiedView, SideBySide },
  setup() {
    const diff = new Diff();

    const result = diff.main(text.old, text.new);
    diff.cleanupSemantic(result);

    const code = ref(true);

    const unified = ref(true);

    return { code, result, unified };
  },
};
</script>

