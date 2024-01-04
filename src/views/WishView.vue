<template>
  <div class="container mt-60 py-60">
    <h2 class="fw-bolder">願望清單</h2>

    <table class="table table-hover table-responsive align-middle">
      <thead>
        <tr>
          <th scope="col">產品圖片</th>
          <th scope="col">產品名稱</th>
          <th scope="col">產品價格</th>
          <th scope="col">操作</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="item in wishList" :key="item.id">
          <th scope="row">
            <img :src="item.image" :alt="item.title" :style="{ width: `50px`, height: `50px` }" />
          </th>
          <td>{{ item.title }}</td>
          <td>
            <div class="text-decoration-line-through text-muted">$NT{{ item.origin_price }}</div>
            <div class="fw-bolder">$NT{{ item.price }}</div>
          </td>
          <td>
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
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  data() {
    return {
      wishList: []
    };
  },
  methods: {
    loadWishes() {
      const storedWishes = localStorage.getItem('wishList');
      if (storedWishes) {
        this.wishList = JSON.parse(storedWishes);
      }
    },
    addToWishList(product) {
      const index = this.wishList.find((item) => item.id === product.id);
      if (index) {
        this.wishList = this.wishList.filter((wish) => wish.id !== product.id);
      } else {
        this.wishList.push(product);
      }
    },
    addToCart() {},
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
  },
  mounted() {
    this.loadWishes();
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
