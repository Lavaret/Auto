<template>
  <section class="wrapper" :style="style">
    <img class="car-logo" :src="logo" :alt="car.manufacturer"/>
    <div class="model">{{car.manufacturer}} {{car.model}}</div>
  </section>
</template>

<script>
export default {
  name: 'Car',
  props: {
    car: {
      type: Object,
      required: true,
    },
  },
  computed: {
    logo() {
      const images = require.context('../assets/logos', false, /\.png$/);
      return images(`./${this.car.manufacturer.toLowerCase()}.png`);
    },
    style() {
      const images = require.context('../assets', false, /\.png$/);
      const url = images(`./${this.car.image}`);
      console.log(images, url);
      return `backgroundImage: url("${url}")`;
    },
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  top: 0;
  width: 250px;
  height: 250px;
  background-size: contain;
  background-position: center;
  background-repeat: no-repeat;
  transition: .5s ease;
  position: relative;
  text-align: center;
  border-radius: 8px;

  &:hover {
    -moz-box-shadow: 0px 0px 33px -2px rgba(0,0,0,.3);
    box-shadow: 0px 0px 33px -2px rgba(0,0,0,.3);
    -webkit-box-shadow: 0px 0px 33px -2px rgba(0,0,0,0.3);
    cursor: pointer;
  }

  &:hover .car-logo{
    opacity: 1;
  }

  &:hover .model {
    opacity: .7;
  }
}

.car-logo {
  max-height: 60px;
  max-width: 60px;
  transition: .5s ease;
  opacity: 0;
  position: absolute;
  top: 15%;
  left: 85%;
  transform: translate(-50%, -50%);
  -ms-transform: translate(-50%, -50%);
}

.model {
  bottom: 0%;
  height: 20%;
  width: 100%;
  transition: .5s ease;
  position: absolute;
  text-transform: uppercase;
  font-size: 20px;
  opacity: 0;
}
</style>
