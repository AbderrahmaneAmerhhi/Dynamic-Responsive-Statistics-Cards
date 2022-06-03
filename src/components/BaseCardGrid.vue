<template>
  <div class="container-fluid px-4">
    <div class="row g-3 my-2">
      <div class="cadr col-md-3" v-for="(data, index) in data" :key="index">
        <!-- <BaseCard :title="data.title" :number="data.number" :icon="data.icon" /> -->
        <BaseCard v-bind="data" />
      </div>
    </div>
  </div>
</template>

<script>
import BaseCard from "./BaseCard.vue";
export default {
  mounted() {
    this.CounterAnimation();
  },
  props: ["data"],
  name: "cards",
  methods: {
    // stat cards Counte up animation
    CounterAnimation() {
      const counters = document.querySelectorAll(".counter");
      counters.forEach((counter) => {
        counter.innerText = "0";
        const UpdateCounter = () => {
          const target = +counter.getAttribute("data-target");
          const c = +counter.innerText;
          const increment = target / 200;
          if (c < target) {
            counter.innerText = `${Math.ceil(c + increment)}`;
            setTimeout(UpdateCounter, 1);
          }
        };
        UpdateCounter();
      });
    },
  },
  components: { BaseCard },
};
</script>

<style>
.cadr {
  position: relative;
}
.cadr::before {
  content: "";
  width: 6px;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  background-color: #232d65;
}

.cadr:hover::before {
  background-color: #929dd9;
}
.cadr:hover .card-icon {
  background-color: #a8b0e0;
}
</style>
