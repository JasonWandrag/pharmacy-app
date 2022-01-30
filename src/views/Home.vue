<template>
  <header class="landing">
    <div class="landing-text">
      <h1>Online Pharmacy</h1>
      <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Optio, sit
        corporis! Id, et quidem? Nemo error, dolorum perspiciatis tempore nobis,
        assumenda omnis eligendi iste, a fugiat totam sit corporis minus!
      </p>
      <router-link class="landing-btn" :to="{ name: 'Products' }"
        >Browse Products</router-link
      >
    </div>
    <img class="landing-img" src="@/assets/TeleMedicine.png" alt="Landing" />
  </header>
</template>

<script lang="ts">
import { Options, Vue } from "vue-class-component";

@Options({
  components: {},
})
export default class Home extends Vue {}
</script>

<style lang="scss">
.landing {
  display: flex;
  align-items: center;
  padding: 2% 10%;
}
.landing-img {
  max-height: 70vh;
  object-fit: contain;
}
.landing-img,
.landing-text {
  width: 50%;
}
.landing-text {
  text-align: left;
}

.landing-text h1 {
  text-transform: uppercase;
  font-size: 4rem;
  line-height: 3.5rem;
  margin-bottom: 30px;
}

.landing-text p {
  margin-bottom: 30px;
}

.landing-text .landing-btn {
  border-radius: 30px;
  background: #f5f5f5;
  box-shadow: 8px 8px 15px #e4e4e4, -8px -8px 15px #ffffff;
  padding: 20px;
  border: none;
  outline: none;
  text-decoration: none;
  color: #333;
}

@media screen and (max-width: 500px) {
  .landing {
    flex-direction: column;
  }
  .landing-img,
  .landing-text {
    width: 100%;
  }
  .landing-text h1 {
    font-size: 2rem;
  }
}
</style>
