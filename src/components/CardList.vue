<script>
import {store} from '../store.js';
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
      <div class="container">
         <div class="row">
            <div class="col">
               <Card/>
            </div>
         </div>
      </div>
</template>

<style lang="scss" scoped>

   

</style>