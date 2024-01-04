<template>
  <div class="container recycling-container px-0 pb-60">
    <div class="row flex-column flex-md-row">
      <div class="col-lg-8">
        <img :src="img" alt="" class="recycling-img" />
      </div>
      <div class="col-lg-4 py-2">
        <div class="d-flex flex-column align-items-start justify-content-center h-100">
          <h4 class="fs-2 fw-bolder">{{ title }}</h4>
          <h5 class="pb-3">{{ subtitle }}</h5>
          <p>{{ text }}</p>
          <router-link to="/">查看更多</router-link>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      img: 'https://images.unsplash.com/photo-1594913615593-e4b8c44625be?q=80&w=1740&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
      title: 'Bottle-Recycling',
      subtitle: 'Recycle your used empty bottles and be rewarded!',
      text: 'For the past 10 years, we have collected over 800,000 bottles through Empty Bottle Recycling Campaign and planted more than 860 pine trees for a better environment.For the past 10 years, we have collected over 800,000 bottles through Empty Bottle Recycling Campaign and planted more than 860 pine trees for a better environment.'
    };
  }
};
</script>

<style lang="scss">
.recycling-container {
  overflow-x: hidden;
  width: 1110px;
  @media (max-width: 375px) {
    width: 100%;
    padding-left: 15px !important;
    padding-right: 15px !important;
  }
}
.recycling-img {
  width: 100%;
  display: block;
  object-fit: cover;

  @media (max-width: 375px) {
    height: 520px;
  }
}
</style>
