<template>
  <div>
    <h1>Photo Gallery with Nuxt</h1>
    <button @click="viewPhotos">View photos</button>
    <ul>
      <li v-for="photo in photoGallery" :key="`photo-id-${photo.id}`">
        <img :src="photo.thumbnailUrl" alt="">
        <!-- <p>{{ photo.thumbnailUrl }}</p> -->
      </li>
    </ul>
  </div>
</template>


<script>
import { defineNuxtComponent } from '#app';

export default defineNuxtComponent ({
  data: () => ({
    photoGallery: []
  }),
  methods: {
    viewPhotos() {
      fetch('https://jsonplaceholder.typicode.com/photos/')
        .then(response => response.json())
        .then(json => {
          this.photoGallery = json;
        })
    }
  }

})

</script>
