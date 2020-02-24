<template>
  <div class="home">
    <h1>Business Wheel</h1>

    <p>La Business Wheel è uno strumento semplice
      ma efficace per rilevare lo scenario della tua azienda.</p>

    <router-link :to="{ name: 'assessment' }">Crea lo scenario adesso!</router-link>
  </div>
</template>

<script>
import { event } from '@/utils/event';

export default {
  name: 'Home',

  created() {
    event.$emit('reset-wheel');
  },
};
</script>
