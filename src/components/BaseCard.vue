<template>
  <div
    class="card p-3 bg-white shadow-sm d-flex flex-row justify-content-around align-items-center rounded"
  >
    <div>
      <h3 class="fs-2">{{ title }}</h3>
      <p class="counter fs-5" v-bind:data-target="number">
        {{ number }}
      </p>
    </div>
    <i :class="`fs-1 border p3 card-icon ${icon ? icon : 'bx bx-stats'}`"></i>
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

  mounted() {
    this.CounterAnimation();
  },

  methods: {
    // there's a bug in the counter animation.
    // it's not working properly.
    // there's a better way to do this.
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
};
</script>

<style scoped>
.card {
  position: relative;
}

.card::before {
  content: "";
  width: 6px;
  height: 100%;
  position: absolute;
  left: 0;
  top: 0;
  background-color: #232d65;
}

.card:hover::before {
  background-color: #929dd9;
}
.card:hover .card-icon {
  background-color: #a8b0e0;
}
.card-icon {
  width: 60px;
  height: 60px;
  display: grid;
  text-align: center;
  align-items: center;
  background-color: #929dd9;
  color: #232d65;
  border-radius: 50%;
}
</style>
