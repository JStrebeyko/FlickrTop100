<template>
  <div class="all">
    <top-bar :value="inputValue"
              @input="handleInput"
              @change="handleChange"
              />
    <pic-grid/>
  </div>
</template>

<script>
import TopBar from '../components/TopBar';
import PicGrid from '../components/PicGrid';

const API_KEY = 'ENTER YOUR API KEY HERE'

export default {
  name: 'MainScreen',
  components: {
    TopBar,
    PicGrid
  },
  data() {
    return {
      inputValue: 'dog',

    }
  },
  methods: {
    handleInput(newValue) {
      // this.inputValue = newValue;
      console.log(newValue)
    },
    handleChange(newValue) {
      console.log(`so this is the changed input value: ${newValue}`);
      this.inputValue = newValue;
      this.requestPhotos()
    },
    requestPhotos() {
      const url = `https://api.flickr.com/services/rest/?method=flickr.photos.search&api_key=${API_KEY}&tags=dog&format=json&nojsoncallback=1&auth_token=72157702216843894-8561943a243d5274&api_sig=f2b6d827ddcba64206b10408cea9ae52`
      fetch(url)
        .then(function(response) {
          return response.json();
        })
        .then(function(myJson) {
          console.log(JSON.stringify(myJson));
        });
    }
  }
};
</script>

<style>

</style>
