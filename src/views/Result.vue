<template>
  <article class="result">
    <h1>Il tuo scenario</h1>

    <div class="result__chart-wrapper">
      <Chart
        :chart-data="result"
        :scale="scale"
        :options="resultOptions"
      />
    </div>
    <Share />
  </article>
</template>

<script>
import Chart from '@/components/Chart.vue';
import Share from '@/components/Share.vue';
import { getChartData } from '@/utils/chart';

export default {
  name: 'Result',

  components: {
    Chart,
    Share,
  },

  props: {
    wheelData: {
      type: Object,
      required: true,
    },

    steps: {
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

  computed: {
    result() {
      const { query = {} } = this.$route;

      if (this.isValidResult(query)) {
        return getChartData(query, this.steps);
      }

      return this.chartData;
    },

    resultOptions() {
      return {
        legend: false,

        plugins: {
          labels: false,
        },
      };
    },
  },

  methods: {
    isValidResult(data) {
      return this.steps.every(step => Reflect
        .has(data, step)
        && Number(data[step]) >= this.scale.min
        && Number(data[step]) <= this.scale.max);
    },
  },
};
</script>

<style>
  .result__chart-wrapper {
    max-width: 30rem;
    margin-left: auto;
    margin-right: auto;
  }
</style>
