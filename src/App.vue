<script>
import axios from 'axios';
import { store } from './store.js';
import MyHeader from './components/MyHeader.vue';
import MyFilter from './components/MyFilter.vue';
import CardList from './components/CardList.vue';
import Loading from './components/Loading.vue';

export default {
  components: {
    Loading,
    MyHeader,
    MyFilter,
    CardList,

  },
  data() {
    return {
      store,
    }
  },
  methods: {
    getCards() {

      let urlApi = 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0';

      if (store.selezioneFiltro.length > 0) {
        urlApi += `?archetype={store.selezioneFiltro}`;
      }


      axios.get(urlApi)
        .then(response => {
          this.store.cardListApi = response.data;
          this.store.loading = false;
        });
    },
    getFilter() {
      axios.get("https://db.ygoprodeck.com/api/v7/archetypes.php")
        .then(response => {
          this.store.archetypeListApi = response.data;
          console.log(store.archetypeListApi[0].archetype_name)
        });
    },
  },
  created() {
    this.getCards();
    this.getFilter();
  }
}

</script>

<template>
  <Loading />
  <MyHeader />
  <div class="sfondo">
    <MyFilter @filtraCard="getCards" />
    <CardList />
  </div>
</template>

<style lang="scss">
@use './styles/General.scss' as *;

.sfondo {
  background-color: $marroncino;
}
</style>
