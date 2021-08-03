<template>
  <div class="btn" :class="className">
    {{ data }}
  </div>
</template>

<script>
  export default {
    props: {
      data: String,
      "class-name": {
        type: String,
        default: "btn-base",
      },
      value: String,
    },
  };
</script>

<style></style>
