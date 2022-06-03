<template>
  <div
    class="p-3 bg-white shadow-sm d-flex justify-content-around align-items-center rounded"
  >
    <div>
      <h3 class="fs-2">{{ title }}</h3>
      <p class="counter fs-5" v-bind:data-target="number">
        {{ number }}
      </p>
    </div>
    <i class="fs-1 border p3 card-icon"></i>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    number: Number,
    color: String,
    icon: String,
  },
};
</script>

<style></style>
