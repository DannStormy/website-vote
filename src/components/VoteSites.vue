<template lang="">
  <div class="container">
    <div :class="['each__list', { 'is__first': index === 0, 'is__second': index === 1}]" v-for="eachList, index in sortList" :key="eachList.id">
      <div class="left">
        <p class="website__name">{{eachList.name}}</p>
        <p>{{eachList.description}}</p>
      </div>
      <div class="controls">
        <p class="vote__count">{{eachList.votes}}</p>
        <div class="up__down">
          <button @click="increase(eachList.id)"><img :src=imgUrl1 alt="arrow-up"></button>
          <button @click="decrease(eachList.id)"><img :src=imgUrl2 alt="arrow-down"></button>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import {initialData} from '../data'
import vector1 from '../assets/Vector (1).svg'
import vector2 from '../assets/Vector (2).svg'
export default {
  data: () => ({
    list: initialData,
    imgUrl1: vector1,
    imgUrl2: vector2
  }),
  methods: {
    increase(id){
      const updatedList = this.list.map((eachList) => {
        if (eachList.id === id){
          return {...eachList, votes: eachList.votes + 1}
        }
        return eachList;
      })
      this.list = updatedList;
    },
    decrease(id){
      const updatedList = this.list.map((eachList) => {
        if (eachList.id === id){
          return {...eachList, votes: eachList.votes - 1}
        }
        return eachList;
      })
      this.list = updatedList;
    }
  },
  computed: {
    sortList() {
      return [...this.list].sort((a, b) => b.votes - a.votes);
    }
  }
}
</script>
<style>
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