<template>
  <div class="wrapper">
    <Claim />
    <SearchInput />
    <div class="search">
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '@/components/Claim.vue';
import SearchInput from '@/components/SearchInput.vue';

const API = 'https://images-api.nasa.gov';

export default {
  name: 'Search',
  components: {
    Claim,
    SearchInput,
  },
  data() {
    return {
      searchValue: '',
      results: [],
    }
  },
  methods: {
    handleInput: debounce(function() {
      axios.get(`${API}/search?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
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
    background-image: url('../assets/hero-bg.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
  }
</style>
