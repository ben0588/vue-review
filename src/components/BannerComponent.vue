<template>
  <div class="banner-container position-relative w-100">
    <img
      src="https://images.unsplash.com/photo-1588159343745-445ae0b16383?q=80&w=1332&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D"
      alt=""
      class="banner-bg w-100"
    />
    <div class="position-absolute top-0 start-50 translate-middle-x w-100 h-100">
      <div class="container h-100">
        <div class="row w-100 h-100">
          <div class="col-lg-8"></div>
          <div class="col-lg-4 d-flex flex-column align-items-start justify-content-center">
            <div class="w-100 ps-4">
              <h2 class="fs-40 text-white fw-bolder">Perfume your day</h2>
              <p class="fs-5 text-white text-wrap">
                A perfume is like a piece of clothing, a message, a way of presenting oneself a
                costume that according to the person who wears it.
              </p>

              <router-link to="/products" class="banner-btn btn-primary-hover-dark"
                >Shop now</router-link
              >
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style lang="scss">
.banner-container {
  margin-top: 2rem;

  @media (max-width: 375px) {
    margin-top: 2.6rem;
  }
}

.banner-bg {
  max-height: 870px;
  object-fit: cover;

  @media (max-width: 375px) {
    height: 480px;
    object-position: -50px;
  }
}

.banner-btn {
  max-width: 350px;
  width: 100%;
  height: 60px;
  border: 2px solid #ffffff;
  color: white;
  background: #00000000;
  border-radius: 30px;
  font-size: 2rem;
  font-weight: bolder;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
  text-decoration: none;
}
</style>
