<script setup>
import imageUrl from '../assets/img001.png';
</script>

<template>
  <footer class="footer-container position-relative fixed-bottom">
    <div class="footer-mx-container px-0 h-100">
      <div class="row h-100">
        <div class="col-12 col-lg-4 pt-5 overflow-hidden">
          <div
            class="d-flex flex-column align-items-start justify-content-center h-100 pt-5 px-3 mt-3"
          >
            <h5 class="fs-2 text-secondary mt-5 pt-5 fw-bolder">
              記得 <br />
              訂閱以獲取更多資訊！
            </h5>
            <div class="input-group border border-2 border-primary rounded mt-3">
              <input
                type="text"
                class="form-control custom-input-height"
                placeholder="Your email address"
                aria-label="Recipient's username"
                aria-describedby="button-addon2"
              />
              <button class="btn btn-primary rounded-0 py-2 px-3" type="button" id="button-addon2">
                Subscribe
              </button>
            </div>
          </div>
        </div>
        <div class="col"></div>
        <div class="col"></div>
      </div>
    </div>

    <div class="position-absolute bottom-0 end-0 w-100 bg-primary">
      <div class="footer-mx-container px-0">
        <div
          class="d-flex justify-content-center justify-content-md-between align-items-center w-100 py-3"
        >
          <div :class="['d-flex', 'justify-content-center', 'align-items-center']">
            <img :src="imageUrl" alt="" class="footer-log-img" />
            <div class="footer-sm-text ms-3 pt-2">© 2020. All Rights Reserved.</div>
          </div>

          <nav :class="['w-50', { 'd-none': windowWidth <= 375 }]">
            <ul class="d-flex justify-content-center align-items-center m-0">
              <li
                class="list-unstyled fs-5 text-white px-3"
                v-for="item in footerList"
                :key="item.title"
              >
                <router-link :to="`${item.path}`" class="nav-link nav-link-dark">{{
                  item.title
                }}</router-link>
              </li>
            </ul>
          </nav>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  data() {
    return {
      windowWidth: 0,
      img: 'https://images.unsplash.com/photo-1532413992378-f169ac26fff0?q=80&w=1480&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D',
      footerList: [
        {
          path: '/products',
          title: 'Products'
        },
        {
          path: '/products',
          title: 'Blog'
        },
        {
          path: '/products',
          title: 'Contact'
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
.footer-mx-container {
  overflow-x: hidden;
  width: 1110px;
  margin: 0 auto;
  @media (max-width: 375px) {
    width: 100%;
    padding-left: 15px !important;
    padding-right: 15px !important;
  }
}

.footer-container {
  background-image: url('https://images.unsplash.com/photo-1532413992378-f169ac26fff0?q=80&w=1480&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D');
  background-position: center;
  object-fit: contain;
  height: 600px;
  overflow: hidden;
  position: fixed;
}

.footer-nav-container {
  height: 80px;
}

.custom-input-height {
  height: 60px; /* 設定您期望的高度 */
}

.footer-log-img {
  width: 128px;
  height: 38px;
  display: block;
}

.footer-sm-text {
  font-size: 14px;
  color: #ffffff;
}
</style>
