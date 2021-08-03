<template>
  <div class="flex text-skin-screen justify-between items-center pb-3">
    <h1 class="text-2xl">calc</h1>
    <div
      class="flex justify-between items-end gap-3 text-xs font-thin tracking-wider"
    >
      <div class="uppercase">theme</div>
      <div @click="themeToggle">
        <div class="flex justify-around text-xs">
          <div>1</div>
          <div>2</div>
          <div>3</div>
        </div>
        <div
          class="bg-skin-keypad flex rounded-full p-1 w-14"
          :class="buttonActual"
        >
          <div class="rounded-full w-3 h-3 bg-skin-key-accent-2"></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import { inject, ref } from "@vue/runtime-core";
  export default {
    setup() {
      const theme = inject("theme");
      const buttonMargin = {
        1: "justify-start",
        2: "justify-center",
        3: "justify-end",
      };
      let buttonActual = ref(buttonMargin[1]);
      const themeToggle = () => {
        theme.value === 3 ? (theme.value = 1) : theme.value++;
        buttonActual.value = buttonMargin[theme.value];
      };
      return { themeToggle, buttonActual };
    },
  };
</script>

<style></style>
