<template>
  <div class="my-60">
    <div class="bg-muted py-6" :style="{ backgroundColor: '#E0E0E0' }">
      <div class="container popular-container">
        <div class="row">
          <div
            :class="['col-lg-4', 'ps-0', { 'ps-3': windowWidth <= 375 }]"
            v-for="item in products"
            :key="item.title"
          >
            <div class="card border border-0">
              <div :class="['popular-img', 'card-img-hover', { 'sold-out-img': item.isSold_out }]">
                <img :src="item.img" :class="['popular-img', '']" :alt="item.title" />
              </div>

              <div class="py-2" :style="{ backgroundColor: '#E0E0E0' }">
                <h5 class="card-title fw-bolder fs-5 mb-0">{{ item.title }}</h5>
                <p class="">{{ item.brand }}</p>

                <span>NT${{ item.price }}</span>
                <span v-if="item.isSALE" class="ms-2 text-secondary text-decoration-line-through"
                  >NT${{ item.original_price }}</span
                >
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      windowWidth: 0,
      products: [
        {
          img: 'https://images.unsplash.com/photo-1530630458144-014709e10016?q=80&w=1587&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          title: 'Poppy & Barley',
          brand: 'Jo Malone',
          price: 1380,
          original_price: 1680,
          isSALE: true,
          isSold_out: false
        },
        {
          img: 'https://images.unsplash.com/photo-1556228720-da4e85f25e15?q=80&w=1592&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          title: 'Body Wash',
          brand: 'Curology',
          price: 1580,
          original_price: 1680,
          isSALE: false,
          isSold_out: false
        },
        {
          img: 'https://images.unsplash.com/photo-1559264730-1533a6ec0433?q=80&w=1635&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
          title: 'Apple Cider Vinegar Capsule',
          brand: 'Tonik',
          price: 1580,
          original_price: 1680,
          isSALE: false,
          isSold_out: true
        }
      ]
    };
  },
  mounted() {
    this.windowWidth = window.innerWidth;
    window.addEventListener('resize', () => {
      this.windowWidth = window.innerWidth;
    });
  }
};
</script>

<style lang="scss">
.popular-container {
  overflow-x: hidden;
  width: 1110px;
  @media (max-width: 375px) {
    width: 100%;
  }
}

.popular-img {
  object-fit: cover;
  object-position: center;
  width: 100%;
  height: 540px;
  position: relative;
  display: block;

  @media (max-width: 375px) {
    height: 350px;
    object-position: bottom;
  }
}

/* .popular-img-container {
  @media (max-width: 375px) {
    padding-left: 5px;
    padding-right: 5px;
  }
} */

.sold-out-img {
  &::before {
    content: 'Sold out';
    position: absolute;
    width: 100%;
    height: 100%;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    background: #0000005e;
    /* opacity: 0.3; */
    z-index: 100;
    color: white;
    text-align: center;
    font-size: 1.5rem;
    display: flex;
    align-items: center;
    justify-content: center;
  }
}
</style>
