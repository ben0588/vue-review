<template>
  <div class="mt-60">
    <div class="bg-primary">
      <div class="container">
        <ul
          class="list-unstyled d-none d-md-flex justify-content-start align-items-center m-0 py-1"
        >
          <li v-for="nav in navList" :key="nav.title">
            <router-link to="/" class="nav-link-dark text-white d-block fs-5 py-2 pe-4">{{
              nav.title
            }}</router-link>
          </li>
        </ul>
      </div>
    </div>

    <div class="mt-80">
      <div class="container">
        <div class="row row-cols-2 row-cols-md-4 g-2 g-sm-2 px-0">
          <div class="col" v-for="item in products" :key="item.id">
            <div class="products-cred border border-0">
              <div class="card-img-container">
                <img :src="item.image" class="products-img" :alt="item.title" />
              </div>
              <div class="card-body pt-1 ps-0 pb-5">
                <h5 class="card-title fw-bolder m-0">{{ item.title }}</h5>
                <p class="card-text m-0">
                  {{ item.category }}
                </p>
                <div class="mb-1">
                  NT${{ item.price
                  }}<span class="text-muted text-decoration-line-through ms-2"
                    >NT${{ item.origin_price }}</span
                  >
                </div>
                <span @click.prevent="addToWishList(item)">
                  <font-awesome-icon
                    :icon="['fas', 'heart']"
                    size="lg"
                    :class="[
                      { 'text-primary': !isWishListed(item) },
                      { 'text-danger': isWishListed(item) }
                    ]"
                  />
                </span>
                <span @click.prevent="addToCart(item)">
                  <font-awesome-icon
                    :icon="['fas', 'cart-shopping']"
                    size="lg"
                    class="text-primary ms-2"
                  />
                </span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div class="d-flex justify-content-center align-items-center mb-5">
      <nav aria-label="Page navigation example border-0">
        <ul class="pagination">
          <li class="page-item">
            <!-- <a class="page-link border-0" href="#" aria-label="Previous">
              <span aria-hidden="true">&laquo;</span>
            </a> -->
          </li>
          <li class="page-item">
            <a class="page-link border-0 text-decoration-underline" href="#">1</a>
          </li>
          <li class="page-item"><a class="page-link border-0" href="#">2</a></li>
          <li class="page-item"><a class="page-link border-0" href="#">3</a></li>
          <li class="page-item">
            <!-- <a class="page-link border-0" href="#" aria-label="Next">
              <span aria-hidden="true">&raquo;</span>
            </a> -->
          </li>
        </ul>
      </nav>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      navList: [
        { title: 'CHANEL' },
        { title: 'Jo Malone' },
        { title: 'Curology' },
        { title: 'Dior' },
        { title: 'Chloe' },
        { title: 'ZARA' }
      ],
      products: [],
      wishList: []
    };
  },
  mounted() {
    this.loadWishes();
    this.$http.get(import.meta.env.VITE_API_PATH).then((response) => {
      this.products = response.data.products;
    });
  },
  methods: {
    loadWishes() {
      const storedWishes = localStorage.getItem('wishList');
      if (storedWishes) {
        this.wishList = JSON.parse(storedWishes);
      }
      console.log(this.wishList);
    },
    addToWishList(product) {
      const index = this.wishList.find((item) => item.id === product.id);
      if (index) {
        this.wishList = this.wishList.filter((wish) => wish.id !== product.id);
      } else {
        this.wishList.push(product);
      }
    },
    addToCart(product) {
      console.log('cart', product);
    },
    isWishListed(item) {
      // 使用 some() 方法來檢查願望清單中是否有 item 的 id
      return this.wishList.some((wishItem) => wishItem.id === item.id);
    }
  },
  watch: {
    // 監聽 wishList 的變化
    wishList: {
      deep: true, // 深度監聽，即使是物件或陣列內部的變化也能檢測到
      handler(newVal) {
        // 當 wishList 更新時，將其儲存到 localStorage
        localStorage.setItem('wishList', JSON.stringify(newVal));
      }
    }
  }
};
</script>

<style lang="scss">
.products-cred {
  overflow: hidden;
  cursor: pointer;
  transition: 0.2s ease-in-out;

  &:hover {
    /* pointer-events: none; */
    opacity: 0.85;
  }
}

.card-img-container {
  width: 255px;
  height: 255px;
  @media (max-width: 375px) {
    height: 165px;
    width: 165px;
  }
}

.products-img {
  width: 100%;
  height: 100%;
  display: block;
  object-fit: cover;
  object-position: center;

  @media (max-width: 375px) {
    height: 165px;
    width: 165px;
  }
}
</style>
