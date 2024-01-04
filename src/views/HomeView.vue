<script>
import BannerComponent from '@/components/BannerComponent.vue';
import RecommendComponent from '@/components/RecommendComponent.vue';
import PopularComponent from '@/components/PopularComponent.vue';
import RecyclingComponent from '@/components/RecyclingComponent.vue';

export default {
  components: {
    BannerComponent,
    RecommendComponent,
    PopularComponent,
    RecyclingComponent
  }
};
</script>

<template>
  <main>
    <BannerComponent></BannerComponent>
    <RecommendComponent></RecommendComponent>
    <PopularComponent></PopularComponent>
    <RecyclingComponent></RecyclingComponent>
  </main>
</template>
