<script>
import {store} from '../store';
import Card from './Card.vue';
export default {
   name: "CardList",
   components: {
      Card
   },
   data() {
      return {
         store
      }
   },
}
</script>

<template>
      <div class="container py-5">
         <div class="row p-5 bg-white">
            <div class="col-2 px-1" v-for="(carta, index) in store.cardListApi.data" :key="index">
               <Card
               :image="carta.card_images[0].image_url"
               :name="carta.name"
               :type="carta.type"
               />
            </div>
         </div>
      </div>
</template>

<style lang="scss" scoped>

   

</style>


