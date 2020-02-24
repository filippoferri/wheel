<template>
  <Step
    class="step"
    :title="steps[currentStep]"
    :desc="descriptions[currentStep]"
    :step="currentStep"
    :value="currentStepValue"
    :scale-max="scaleMax"
    @set-value="next">
    <p>Come giudichi quest'aspetto del tuo business?</p>
  </Step>
</template>

<script>
import Step from '@/components/Stepper/Step.vue';
import { event } from '@/utils/event';

export default {
  name: 'Stepper',

  components: {
    Step,
  },

  data() {
    return {
      currentStep: 0,
    };
  },

  props: {
    steps: {
      type: Array,
      required: true,
    },

    descriptions: {
      type: Array,
      required: true,
    },

    wheelData: {
      type: Object,
      required: true,
    },

    scaleMax: {
      type: Number,
      default: 10,
    },
  },

  computed: {
    currentStepValue() {
      return this.wheelData[this.steps[this.currentStep]];
    },
  },

  methods: {
    next(val) {
      event.$emit('set-wheel', {
        [this.steps[this.currentStep]]: val,
      });

      this.currentStep += 1;

      if (this.currentStep > this.steps.length - 1) {
        this.$emit('show-result');
      }
    },
  },
};
</script>

<style lang="scss">
.step {
  margin-top: 2rem;
}
</style>
