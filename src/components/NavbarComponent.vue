<template>
  <header class="fixed-top bg-white shadow-sm" :style="{ height: `54px` }">
    <nav
      class="container d-flex align-items-center justify-content-between navbar navbar-expand-lg bg-white py-1 w-100 px-3"
    >
      <div class="d-flex align-items-center justify-content-between w-sm-100">
        <router-link to="/" class="d-block">
          <img
            src="https://cdn-sharing.adobecc.com/content/storage/id/urn:aaid:sc:US:dc5ebe5c-3e56-4981-a010-158b5ded0e72;revision=1?component_id=548f8c4c-e2fc-4a91-827a-2ec00d4b9efc&api_key=CometServer1&access_token=1704385423_urn%3Aaaid%3Asc%3AUS%3Adc5ebe5c-3e56-4981-a010-158b5ded0e72%3Bpublic_03bec2ae7bec02c218f9d0f2c5bee51d011e275c"
            alt="電商網站"
          />
        </router-link>

        <div class="d-flex justify-content-center align-items-center">
          <a
            class="nav-link fs-5 fw-bolder position-relative pe-4 mt-2"
            href="#"
            v-if="flexRowReverse"
            ><font-awesome-icon :icon="['fas', 'cart-shopping']" />
            <span
              class="position-absolute top-0 start-50 translate-middle p-2 bg-primary border border-light rounded-circle d-flex justify-content-center align-items-center mt-1"
              :style="{
                fontSize: '12px',
                width: `16px`,
                height: `13px`,
                color: 'white',
                border: 'none'
              }"
            >
              2
            </span></a
          >
          <button
            class="navbar-toggler"
            type="button"
            data-bs-toggle="collapse"
            data-bs-target="#navbarNavDropdown"
            aria-controls="navbarNavDropdown"
            aria-expanded="false"
            aria-label="Toggle navigation"
          >
            <span class="navbar-toggler-icon"></span>
          </button>
        </div>
      </div>

      <div class="d-flex align-items-center justify-content-end">
        <div class="collapse navbar-collapse w-100" id="navbarNavDropdown">
          <ul class="navbar-nav">
            <li class="nav-item">
              <router-link to="products" class="nav-link fs-5 fw-bolder"
                ><font-awesome-icon :icon="['fas', 'shop']" class="md-icon" />Product</router-link
              >
            </li>
            <li class="nav-item">
              <a class="nav-link fs-5 fw-bolder" href="#"
                ><font-awesome-icon :icon="['fas', 'user']" class="md-icon" />log in</a
              >
            </li>
            <li class="nav-item">
              <router-link to="/wishlist" class="nav-link fs-5 fw-bolder"
                ><font-awesome-icon :icon="['fas', 'heart']" class="md-icon" />Wishlist</router-link
              >
            </li>
            <li class="nav-item">
              <a class="nav-link fs-5 fw-bolder" href="#"
                ><font-awesome-icon :icon="['fas', 'cart-shopping']" class="md-icon" />Cart (3)</a
              >
            </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>

<script>
import 'bootstrap/dist/js/bootstrap.bundle.min.js';

export default {
  data() {
    return {
      windowWidth: 0
    };
  },
  computed: {
    flexRowReverse() {
      return this.windowWidth <= 992 ? true : false;
    }
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
.w-sm-100 {
  @media (max-width: 992px) {
    width: 100%;
  }
}
</style>
