<script>
import axios from 'axios';
import { store } from './store.js';
import MyHeader from './components/MyHeader.vue';
import CardList from './components/CardList.vue';
import Loading from './components/Loading.vue';

export default {
  components: {
    Loading,
    MyHeader,
    CardList,
  },
  data() {
    return {
      store
    }
  },
  methods: {
    getCards() {
      axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=Blue-Eyes')
        .then(response => {
          this.store.cardListApi = response.data;
          this.store.loading = false;
        });
    }
  },
  created() {
    this.getCards();
  }
}

</script>

<template>
  <Loading />
  <MyHeader />
  <div class="sfondo">
    <CardList />
  </div>
</template>

<style lang="scss">
@use './styles/General.scss' as *;

.sfondo {
  background-color: $marroncino;
}
</style>
