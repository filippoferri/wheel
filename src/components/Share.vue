<template>
  <section class="share">
    <p>Vuoi monitorare la Business Wheel nel tempo? Contattaci per avere il tuo
      scenario sempre sotto controllo e per avviare strategie
      di miglioramento delle aree più critiche.</p>
  </section>
</template>

<script>
export default {
  name: 'Share',
};
</script>

<style lang="scss">
  .share {
    user-select: none;

    &__list {
      list-style: none;
      padding: 0;
      margin-left: -.5rem;
      margin-right: -.5rem;
    }

    &__item {
      display: inline-block;
      margin: 0 .5rem;
    }
  }
</style>
