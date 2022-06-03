<template>
  <div class="container-fluid px-4">
    <div class="row g-3 my-2">
      <template v-for="(data, index) in data">
        <div class="col-md-3" :key="index">
          <!-- <BaseCard :title="data.title" :number="data.number" :icon="data.icon" /> -->

          <!-- Use spread operator to pass down props --->
          <BaseCard v-bind="data" />
        </div>
      </template>
    </div>
  </div>
</template>

<script>
import BaseCard from "./BaseCard.vue";
export default {
  props: {
    data: {
      type: Array,
      default: () => [],
      required: true,
    },
  },

  components: { BaseCard },
};
</script>
