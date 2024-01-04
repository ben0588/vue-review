<script>
import NavbarComponent from './components/NavbarComponent.vue';
import FooterComponent from './components/FooterComponent.vue';

export default {
  components: {
    NavbarComponent,
    FooterComponent
  }
};
</script>

<template>
  <NavbarComponent></NavbarComponent>

  <router-view></router-view>

  <FooterComponent></FooterComponent>
</template>

<style lang="scss">
@import './assets/all.scss';
</style>
