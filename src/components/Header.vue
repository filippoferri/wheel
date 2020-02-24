<template>
  <nav class="links">
    <router-link to="/" class="links__item">Home</router-link>
    <router-link to="/assessment" class="links__item">Inizia</router-link>
  </nav>
</template>

<script>
export default {
  name: 'Header',
};
</script>

<style lang="scss">
  .links {
    display: flex;

    &__item {
      padding: 0 .5rem;
      display: inline-block;
      vertical-align: top;
    }
  }
</style>
