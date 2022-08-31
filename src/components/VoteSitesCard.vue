<template>
  <div class="container">
    <div :class="['each__list', { 'is__first': isFirst, 'is__second': isSecond}]">
      <div class="left">
        <p class="website__name">{{name}}</p>
        <p>{{description}}</p>
      </div>
      <div class="controls">
        <p class="vote__count">{{votes}}</p>
        <div class="up__down">
          <button @click="increase()"><img :src=img1 alt="arrow-up"></button>
          <button @click="decrease()"><img :src=img2 alt="arrow-down"></button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: ['name', 'description', 'votes', 'id', 'index', 'img1', 'img2'],
  computed: {
    isFirst() {
      return this.index === 0;
    },
    isSecond() {
      return this.index === 1;
    }
  },
  methods: {
    increase(){
      this.$emit('increase')
    },
    decrease(){
      this.$emit('decrease')
    }
  }
}
</script>
<style scoped>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }
  body {
    background-color: #D3D3D3;
  }
  .each__list {
    display: flex;
    justify-content: space-between;
    background-color: white;
    width: 641px;
    height: 72px;
    border-radius: 8px;
    margin:  0 auto;
    margin-bottom: 10px;
    padding: 10px 20px;
    border: 3px solid #CDCDCD;
  }
  .is__first{
    border: 3px solid #3FB961;
  }
  .is__second {
    border: 3px solid #F8D34F;
  }
  .website__name{
    margin-bottom: 6px;
    font-weight: 600;
  }
  .vote__count{
    width: 48px;
    height: 44px;
    background: #EFEFEF;
    border-radius: 8px;
    font-weight: 600;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .controls{
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 90px;
  }
  .up__down{
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    height: 44px;
  }
  button{
    border: none;
    background-color: transparent;
  }
</style>