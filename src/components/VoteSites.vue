<template>
  <div class="container">
    <VoteSitesCard
    v-for="eachList, index in sortList"
    :key="eachList.id"
    :id="eachList.id"
    :index="index"
    :name="eachList.name"
    :description="eachList.description"
    :votes="eachList.votes"
    :img1=imgUrl1
    :img2=imgUrl2
    @increase="increase(eachList.id)"
    @decrease="decrease(eachList.id)"
    >
    </VoteSitesCard>
  </div>
</template>
<script>
import {initialData} from '../data'
import VoteSitesCard from './VoteSitesCard.vue'
import vector1 from '../assets/Vector (1).svg'
import vector2 from '../assets/Vector (2).svg'

export default {
    data: () => ({
        list: initialData,
        imgUrl1: vector1,
        imgUrl2: vector2
    }),
    methods: {
        increase(id) {
            const updatedList = this.list.map((eachList) => {
                if (eachList.id === id) {
                    return { ...eachList, votes: eachList.votes + 1 };
                }
                return eachList;
            });
            this.list = updatedList;
        },
        decrease(id) {
            const updatedList = this.list.map((eachList) => {
                if (eachList.id === id) {
                    return { ...eachList, votes: eachList.votes - 1 };
                }
                return eachList;
            });
            this.list = updatedList;
        }
    },
    computed: {
        sortList() {
            return [...this.list].sort((a, b) => b.votes - a.votes);
        }
    },
    components: { VoteSitesCard }
}
</script>
<style>
  /* *{
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
  } */
</style>