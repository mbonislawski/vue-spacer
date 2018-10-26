<template>
  <div :class="[{ flexStart: step === 1}, 'wrapper']">
    <transition name="slide">
      <img src="../assets/logo.png" class="logo" v-if="step === 1">
    </transition>
    <transition name="fade">
      <HeroImage v-if="step === 0"  />
    </transition>
    <Claim v-if="step === 0" />
    <SearchInput v-model="searchValue" @input="handleInput" :dark="step === 1" />
    <div class="results" v-if="results && !loading && step === 1">
      <Item v-for="item in results" :item="item" :key="item.data[0].nasa_id" @click.native="handleModalOpen(item)" />
    </div>
    <div class="loader" v-if="loading && step === 1"><div></div><div></div></div>
    <Modal v-if="modalOpen" :item="modalItem" @closeModal="modalOpen = false" />
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';
import HeroImage from '@/components/HeroImage.vue';
import Item from '@/components/Item.vue';
import Modal from '@/components/Modal.vue';

const API = 'https://images-api.nasa.gov';

export default {
  name: 'Search',
  components: {
    Claim,
    SearchInput,
    HeroImage,
    Item,
    Modal,
  },
  data() {
    return {
      modalOpen: false,
      modalItem: null,
      loading: false,
      step: 0,
      searchValue: '',
      results: [],
    }
  },
  methods: {
    handleModalOpen(item) {
      this.modalOpen = true;
      this.modalItem = item;
    },
    handleInput: debounce(function() {
      this.loading = true;
      axios.get(`${API}/search?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
          this.loading = false;
          this.step = 1;
        })
        .catch((error) => {
          console.log(error);
          });
    }, 500),
  },
};
</script>
<style lang="scss" scoped>
  .wrapper {
    width: 100%;
    height: 100vh;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    margin: 0;
    padding: 30px;
    margin: 0;
    position: relative;

    &.flexStart {
      justify-content: flex-start;
    }
  }

  .logo {
    position: absolute;
    top: 30px;
    max-width: 30px;
  }

  .slide-enter-active, 
  .slide-leave-active {
    transition: margin-top .3s ease;
  }

.slide-enter, 
.slide-leave-to
/* .slide-leave-active below version 2.1.8 */ {
  margin-top: -50px;
}

.results {
  margin-top: 150px;
  position: relative;
  width: 100%;
  display: grid;
  grid-template-columns: 1fr;
  grid-gap: 20px;
  @media(min-width: 768px) {
    grid-template-columns: 1fr 1fr;
    width: 80%;
  }
  @media(min-width: 1024px) {
    grid-template-columns: 1fr 1fr 1fr;
  }

  p {
    color: #000;
  }
}

.loader {
  margin-top: 100px;
  display: inline-block;
  position: relative;
  width: 64px;
  height: 64px;
}
.loader div {
  position: absolute;
  border: 4px solid #000;
  opacity: 1;
  border-radius: 50%;
  animation: loading 1s cubic-bezier(0, 0.2, 0.8, 1) infinite;
}
.loader div:nth-child(2) {
  animation-delay: -0.5s;
}
@keyframes loading {
  0% {
    top: 28px;
    left: 28px;
    width: 0;
    height: 0;
    opacity: 1;
  }
  100% {
    top: -1px;
    left: -1px;
    width: 58px;
    height: 58px;
    opacity: 0;
  }
}
</style>
