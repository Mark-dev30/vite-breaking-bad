<script>

import axios from 'axios';
import AppHeader from './components/AppHeader.vue';
import AppMain from './components/AppMain.vue';
import { store } from './store.js';

export default {
  components: {
    AppHeader,
    AppMain,
  },
  data() {
    return {
      store,
    }
  },
  beforeMount() {
    this.getUrlCards();
  },
  methods: {
    getUrlCards() {
      axios.get(store.url).then((response) => {
        store.arraycards = response.data.data
        store.arraylenght = store.arraycards.length
        setTimeout(() => {
          store.loading_page = false
        }, 2000)

      })
    }
  }
}
</script>
<template lang="">
  <div>
    <AppHeader></AppHeader>
    <AppMain></AppMain>
  </div>
</template>

<style lang="scss">
@use './styles/generals.scss' as *;
</style>