<template>
  <div
    class="absolute left-0 right-0 bg-skin-base flex flex-col items-center justify-center h-max min-h-full overflow-x-auto"
    :class="`theme-${theme}`"
  >
    <div class="my-auto md:min-h-4/5 md:w-2/5 w-4/5 min-h-9/10 relative p-6">
      <header-calc />
      <screen-calc />
      <keys-calc />
    </div>
  </div>
</template>

<script>
  import { reactive, ref } from "@vue/reactivity";
  import HeaderCalc from "./components/HeaderCalc.vue";
  import ScreenCalc from "./components/ScreenCalc.vue";
  import KeysCalc from "./components/KeysCalc.vue";
  import { provide } from "@vue/runtime-core";
  export default {
    components: { HeaderCalc, ScreenCalc, KeysCalc },

    setup() {
      const theme = ref(1);
      provide("theme", theme);
      const screen = reactive([]);
      provide("screen", screen);
      return { theme };
    },
  };
</script>
