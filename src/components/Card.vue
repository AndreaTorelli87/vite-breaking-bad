<script>

import {store} from '../store';
export default {
   name: "Card",
   props:{
      image: String,
      name: String,
      type: String
   },
   data() {
      return {
         store
      }
   },
}
</script>

<template>
   <div class="card">
      <h1>Prova Card</h1>
      <img :src="image" alt="`Immagine ${name}`">
      <h5 class="">{{ name }}</h5>
      <span class="">{{ type }}</span>
   </div>
</template>

<style></style>