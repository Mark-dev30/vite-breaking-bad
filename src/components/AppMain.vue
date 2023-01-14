<script>
import AppContainCard from '../components/AppContainCard.vue';
export default {
  components: {
    AppContainCard
  }
}
</script>
<template lang="">
  <main>
    <div class="container-fluid">
      <div class="row margin-auto">
        <div class="col-8">
            <select name="archetype" id="archetype">
              <option value="alien">Alien</option>
            </select>
        </div>
      </div>
      <div class="row background-white mt-4">
          <div class="col-12">
            <AppContainCard></AppContainCard>
          </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
.container-fluid {
  background-color: #d48f38;

  .margin-auto,
  .background-white {
    width: 90%;
    margin: 0 auto;


    select {
      width: 150px;
      padding: 5px;
      border-radius: 0.4rem;
      margin-top: 30px;
    }
  }
}

.background-white {
  background-color: white;
  margin-top: 30px;
}
</style>