<script>
import { store } from '../store'
import axios from 'axios'
import AppContainCard from '../components/AppContainCard.vue';
import AppSearch from './AppSearch.vue';
export default {
  components: {
    AppContainCard,
    AppSearch
  },
  data() {
    return {
      store
    }
  },
  methods: {
    searchType(word) {
      axios.get(`${store.url}&race=${word}`).then((response) => {
        store.arraycards = response.data.data
        store.arraylenght = store.arraycards.length
      })
    }
  },
}
</script>
<template lang="">
  <main>
    <div  v-if="store.loading_page" class="animation d-flex justify-content-center align-items-center">
      <div>
        <h2>Loading...</h2>
      </div>
      <div class="loader">
        <svg viewBox="0 0 80 80">
          <circle id="test" cx="40" cy="40" r="32"></circle>
        </svg>
      </div>
      <div class="loader triangle">
        <svg viewBox="0 0 86 80">
          <polygon points="43 8 79 72 7 72"></polygon>
        </svg>
      </div>

      <div class="loader">
        <svg viewBox="0 0 80 80">
          <rect x="8" y="8" width="64" height="64"></rect>
        </svg>
      </div>
    </div>
    <div class="container-fluid" v-else>
      <AppSearch @search="searchType" />
      <div class="row background-white mt-4">
          <div class="col-12">
            <AppContainCard></AppContainCard>
          </div>
      </div>
    </div>
  </main>
</template>

<style lang="scss" scoped>
@use '../styles/partials/variables' as *;

.container-fluid {
  background-color: $color_orange;
  padding-bottom: 30px;

  .background-white {
    width: 90%;
    margin: 0 auto;
    background-color: white;
    margin-top: 30px;


    select {
      width: 150px;
      padding: 5px;
      border-radius: 0.4rem;
      margin-top: 30px;
    }
  }
}



/* ANIMATION*/
.animation {
  width: 100%;
  height: calc(100vh - 100px);
  background-image: url(../../public/bg-yu-gi-oh.jpg);
  background-position: center;

  h2 {
    color: white;
  }
}

.loader {
  --path: #099582;
  --dot: #5628ee;
  --duration: 3s;
  width: 44px;
  height: 44px;
  position: relative;
  display: inline-block;
  margin: 0 16px;

  svg {
    display: block;
    width: 100%;
    height: 100%;
  }
}

.loader:before {
  content: '';
  width: 6px;
  height: 6px;
  border-radius: 50%;
  position: absolute;
  display: block;
  background: var(--dot);
  top: 37px;
  left: 19px;
  transform: translate(-18px, -18px);
  animation: dotRect var(--duration) cubic-bezier(0.785, 0.135, 0.15, 0.86) infinite;
}



.loader svg rect,
.loader svg polygon,
.loader svg circle {
  fill: none;
  stroke: var(--path);
  stroke-width: 10px;
  stroke-linejoin: round;
  stroke-linecap: round;
}

.loader svg polygon {
  stroke-dasharray: 145 76 145 76;
  stroke-dashoffset: 0;
  animation: pathTriangle var(--duration) cubic-bezier(0.785, 0.135, 0.15, 0.86) infinite;
}

.loader svg rect {
  stroke-dasharray: 192 64 192 64;
  stroke-dashoffset: 0;
  animation: pathRect 3s cubic-bezier(0.785, 0.135, 0.15, 0.86) infinite;
}

.loader svg circle {
  stroke-dasharray: 150 50 150 50;
  stroke-dashoffset: 75;
  animation: pathCircle var(--duration) cubic-bezier(0.785, 0.135, 0.15, 0.86) infinite;
}

.loader.triangle {
  width: 48px;
}

.loader.triangle:before {
  left: 21px;
  transform: translate(-10px, -18px);
  animation: dotTriangle var(--duration) cubic-bezier(0.785, 0.135, 0.15, 0.86) infinite;
}

@keyframes pathTriangle {
  33% {
    stroke-dashoffset: 74;
  }

  66% {
    stroke-dashoffset: 147;
  }

  100% {
    stroke-dashoffset: 221;
  }
}

@keyframes dotTriangle {
  33% {
    transform: translate(0, 0);
  }

  66% {
    transform: translate(10px, -18px);
  }

  100% {
    transform: translate(-10px, -18px);
  }
}

@keyframes pathRect {
  25% {
    stroke-dashoffset: 64;
  }

  50% {
    stroke-dashoffset: 128;
  }

  75% {
    stroke-dashoffset: 192;
  }

  100% {
    stroke-dashoffset: 256;
  }
}

@keyframes dotRect {
  25% {
    transform: translate(0, 0);
  }

  50% {
    transform: translate(18px, -18px);
  }

  75% {
    transform: translate(0, -36px);
  }

  100% {
    transform: translate(-18px, -18px);
  }
}

@keyframes pathCircle {
  25% {
    stroke-dashoffset: 125;
  }

  50% {
    stroke-dashoffset: 175;
  }

  75% {
    stroke-dashoffset: 225;
  }

  100% {
    stroke-dashoffset: 275;
  }
}
</style>