<template>
  <section class="step">
    <h2 class="step__title">{{ step + 1 }} - {{ title }}</h2>
    <p>{{ desc }}</p>
    <slot></slot>

    <ul class="step__values">
      <template v-for="n in scaleMax">
        <li
          :key="n"
          class="step__value">
          <button
            :class="[
              'step__rate-btn',
              { 'step__rate-btn--active': isSelected(n) },
            ]"
            @click="next(n)">
            {{ n }}
          </button>
        </li>
      </template>
    </ul>

    <!-- button
      class="step__skip-btn"
      @click="skip">
      Skip →
    </button -->
  </section>
</template>

<script>
export default {
  name: 'Step',

  props: {
    title: {
      type: String,
      required: true,
    },
    desc: {
      type: String,
      required: true,
    },
    step: {
      type: Number,
      required: true,
    },
    value: Number,
    scaleMax: Number,
  },

  methods: {
    isSelected(n) {
      return n === this.value;
    },

    skip() {
      this.$emit('set-value', 0);
    },

    next(val) {
      this.$emit('set-value', val);
    },
  },
};
</script>

<style lang="scss">
  .step {
    text-align: center;

    &__title {
      text-transform: capitalize;
    }

    &__values {
      padding: 0;
      list-style: none;
    }

    &__value {
      display: inline-block;
    }

    &__rate-btn {
      font-size: 2rem;
      cursor: pointer;
      background-color: white;

      &--active {
        background-color: #5100FF;
        color: white;
      }
    }
  }
</style>
