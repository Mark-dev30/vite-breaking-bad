<script>
import AppCard from '../components/AppCard.vue';
import { store } from '../store'
export default {
  components: {
    AppCard,

  },
  data() {
    return {
      store
    }
  }
}
</script>
<template lang="">
  <div class="container">
    <div class="row ">
      <div class="col-12">
        <div class="content-result">
          <h4 class="mb-0 p-2">Found {{store.arraylenght}} cards</h4>
        </div>   
        <div class="content-cards d-flex flex-wrap justify-content-between " >
          <AppCard v-for="(item, index) in store.arraycards" :key="index" :character="item"></AppCard>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.content-result {
  background-color: black;
  margin-top: 30px;

  h4 {
    color: white;

  }
}
</style>