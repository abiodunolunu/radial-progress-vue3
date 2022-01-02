<script lang="ts">
import { defineComponent, onMounted, ref } from "vue";
import RadialProgressVue3 from "@/radial-progress-vue3.vue";

export default defineComponent({
  name: "ServeDev",
  components: {
    RadialProgressVue3,
  },
  setup() {
    const percent = ref(42);

    onMounted(() => {
      setInterval(() => {
        percent.value += 3;
      }, 20);
    });

    return {
      percent,
    };
  },
});
</script>

<template>
  <div id="app">
    <radial-progress-vue3 :percent="percent" />
  </div>
</template>
