<template>
  <div class="home">
    <div class="grid">
      <Car />
      <Car />
      <Car />
      <Car />
      <div class="empty">
        <div class="add">+</div>
      </div>
    </div>
  </div>
</template>

<script>

import Car from '@/components/Car.vue';

export default {
  name: 'home',
  components: {
    Car,
  },
};
</script>

<style lang="scss" scoped>
  .home {
    margin-top: 30px;
    min-height: 70vh;
    display: flex;
    justify-content: space-around;
  }

  .grid {
    width: 60vw;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-content: space-evenly;
  }

  .empty {
    width: 250px;
    height: 250px;
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

    &:hover .add {
      opacity: 0.7;
    }
   }

  .add {
    font-size: 50px;
    transition: .5s ease;
    position: absolute;
    top: 40%;
    left: 45%;
    opacity: 0;
  }
</style>
