<template>
  <article class="assessment">
    <Stepper
      :wheel-data="wheelData"
      :steps="steps"
      :descriptions="descriptions"
      :scale-max="scale.max"
      @show-result="showResult" />

    <hr>

    <!-- section class="preview">
      <span class="preview__title">Preview</span>
      <Chart :chart-data="chartData" :scale="scale" />
    </section -->
  </article>
</template>

<script>
import Stepper from '@/components/Stepper/index.vue';
// import Chart from '@/components/Chart.vue';

export default {
  name: 'Assessment',

  props: {
    wheelData: {
      type: Object,
      required: true,
    },

    steps: {
      type: Array,
      required: true,
    },

    descriptions: {
      type: Array,
      required: true,
    },

    chartData: {
      type: Object,
      required: true,
    },

    scale: {
      type: Object,
      required: true,
    },
  },

  components: {
    Stepper,
  },

  methods: {
    showResult() {
      this.$router.push({
        name: 'result',
        query: this.wheelData,
      });
    },
  },
};
</script>

<style lang="scss">
  .preview {
    text-align: center;
    margin-top: 2rem;
    margin-left: auto;
    margin-right: auto;
    max-width: 30rem;

    &__title {
      margin-bottom: 0;
      font-size: 1.5rem;
      font-weight: 700;
    }
  }
</style>
