<template>
  <div
    class="bg-skin-screen rounded-xl text-3xl text-skin-screen p-12 pl-5 pr-5"
  >
    <div class="flex flex-row-reverse overflow-hidden">
      {{ data === "" ? "0" : data }}
    </div>
  </div>
</template>

<script>
  import { inject, ref, watch } from "@vue/runtime-core";
  export default {
    setup() {
      const screen = inject("screen");
      const data = ref("");
      watch(
        () => [...screen],
        (next, prev) => {
          if (
            screen[Object.keys(screen)[Object.keys(screen).length - 1]] === "="
          ) {
            try {
              data.value = eval(prev.join("")).toString();
              screen.length = 0;
              screen.push(...data.value.split(""));
            } catch (err) {
              data.value = err.message;
              setTimeout(() => {
                screen.length = 0;
              }, 1000);
            }
          } else {
            data.value = next.join("");
          }
          data.value = data.value.replace(
            /\B(?<!\.\d*)(?=(\d{3})+(?!\d))/g,
            ","
          );
        },
        { deep: true }
      );
      return { data };
    },
  };
</script>

<style></style>
