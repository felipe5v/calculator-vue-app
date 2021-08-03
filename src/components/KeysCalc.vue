<template>
  <div
    class="bg-skin-keypad rounded-xl grid grid-cols-4 md:gap-6 p-6
  gap-4 mt-4"
  >
    <key
      v-for="(key, idx) in keys"
      :key="idx"
      :data="key.data"
      :class-name="key.class"
      @click="onKeyClick($event)"
      :data-value="key.value ? key.value : key.data"
    />
  </div>
</template>

<script>
  import { inject } from "@vue/runtime-core";
  import Key from "./Key.vue";
  export default {
    components: { Key },
    setup() {
      const keys = [
        { data: "7" },
        { data: "8" },
        { data: "9" },
        { class: "btn-accent-1", data: "del" },
        { data: "4" },
        { data: "5" },
        { data: "6" },
        { data: "+" },
        { data: "1" },
        { data: "2" },
        { data: "3" },
        { data: "-" },
        { data: "." },
        { data: "0" },
        { data: "/" },
        { value: "*", data: "x" },
        { class: "btn-accent-1 w-auto col-span-2 ", data: "reset" },
        { class: "btn-accent-2 w-auto col-span-2", data: "=" },
      ];
      const screen = inject("screen");
      const onKeyClick = (e) => {
        if (e.target.dataset.value === "del") return screen.pop();
        if (e.target.dataset.value === "reset") return (screen.length = 0);

        if (screen.includes(".") && e.target.dataset.value === ".") return;

        screen.push(e.target.dataset.value);
      };
      return { keys, onKeyClick };
    },
  };
</script>

<style></style>
