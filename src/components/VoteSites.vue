<template>
  <div class="container">
    <h2 style="text-align:center">Voting App</h2>
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
</style>