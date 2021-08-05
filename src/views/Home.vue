<template>
  <div class="home">
    <van-swipe class="my_swipe" :autoplay="3000" indicator-color="white">
      <van-swipe-item class="my_swipe_item">
        <div class="imgs_row">
          <img
            class="bg"
            :style="{
              transform: `translate3d(${bg_distanceX}px, ${bg_distanceY}px,${-20}px)`,
            }"
            src="../assets/bg.png"
            alt=""
          />
          <img class="middle" src="../assets/author.png" alt="" />
          <img
            class="prospects"
            :style="{
              transform: `translate3d(${prospects_distanceX}px, ${prospects_distanceY}px,${20}px)`,
            }"
            src="../assets/bg1.png"
            alt=""
          />
        </div>
      </van-swipe-item>
      <van-swipe-item class="my_swipe_item">
        <div class="imgs_row">
          <img
            class="bg"
            :style="{
              transform: `translate3d(${bg_distanceX}px, ${bg_distanceY}px,${-20}px)`,
            }"
            src="../assets/bg.png"
            alt=""
          />
          <img class="middle" src="../assets/author.png" alt="" />
          <img
            class="prospects"
            :style="{
              transform: `translate3d(${prospects_distanceX}px, ${prospects_distanceY}px,${20}px)`,
            }"
            src="../assets/bg1.png"
            alt=""
          />
        </div>
      </van-swipe-item>
    </van-swipe>
  </div>
</template>

<script>
// @ is an alias to /src

export default {
  name: "Home",
  data() {
    return {
      prospects_distanceY: 0,
      bg_distanceY: 0,
      prospects_distanceX: 0,
      bg_distanceX: 0,
    };
  },
  components: {},
  mounted() {
    window.addEventListener("deviceorientation", this.getdirection, false);
  },
  methods: {
    getdirection(res) {
      let displacementX = (res.gamma*0.3).toFixed(1);
      let displacementY = (res.beta*0.3).toFixed(1);

      displacementX = displacementX >= 30 ? 30 : displacementX;
      displacementX = displacementX <= -30 ? -30 : displacementX;
      displacementY = displacementY >= 15 ? 15 : displacementY;
      displacementY = displacementY <= -15 ? -15 : displacementY;
      this.prospects_distanceY = -displacementY;
      this.bg_distanceY = displacementY;
      this.prospects_distanceX = displacementX;
      this.bg_distanceX = -displacementX;
    },
  },
};
</script>

<style lang="scss" scoped>
.imgs_row {
  width: 100vw;
  height: 375px;
  overflow: hidden;
  position: relative;
  display: flex;
  justify-content: center;
  align-items: center;
  perspective: 500;
  -webkit-perspective: 500;
  img {
    position: absolute;
    width: 130%;
    height: 130%;
    &.middle {
      transform: translate3d(0, 0, 0);
    }
  }
}
</style>
