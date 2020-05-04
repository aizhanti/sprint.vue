<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
    <h1>{{ getPhotosFromS3() }}</h1>
    <navbar v-on:view="view" />

    <div v-if="currentView === 'AllView'">
      <div v-for="photo in this.photos" :key="photo.id">
        <allphotos :photo="photo" v-on:getphoto="getphoto" />
      </div>
    </div>
    <div v-else>
      <singlephoto :selectedPhoto="selectedPhoto" />
    </div>
  </div>
</template>

<script>
import Navbar from "./components/Navbar";
import SinglePhoto from "./components/SinglePhoto";
import AllPhotos from "./components/AllPhotos";
import { listObjects, getSingleObject } from "../utils/index.js";

export default {
  name: "App",
  components: {
    navbar: Navbar,
    allphotos: AllPhotos,
    singlephoto: SinglePhoto
  },
  data: () => ({
    title: "",
    currentView: "AllView", ///
    photos: [], ///
    selectedPhoto: "" ///
  }),
  async created() {
    await this.getPhotosFromS3;
  },
  methods: {
    say(message) {
      alert(message);
    },
    view() {
      this.currentView = "AllView";
    },
    getphoto(somePhoto) {
      this.selectedPhoto = somePhoto;
      this.currentView = "SingleView";
      console.log("this.currentView ", this.currentView);
    },
    getPhotosFromS3() {
      // let testArray = [];
      console.log("HELLO World!!");
      listObjects()
        .then(items => {
          let arrayOfPromises = items;
          arrayOfPromises = arrayOfPromises.map(item => {
            return getSingleObject(item.Key);
          });
          let arrayOfResolvedPromises = Promise.all(arrayOfPromises);
          return arrayOfResolvedPromises;
        })
        .then(nextLayer => {
          let arrayOfBase64Strings = nextLayer.map(base64 => {
            return `data:image/jpg;base64, ${base64}`;
          });
          return Promise.all(arrayOfBase64Strings);
        })
        .then(strings2 => {
          this.photos = strings2;
        });
    }
  }
};
</script>

<style>
#app {
  text-align: center;
}
</style>
