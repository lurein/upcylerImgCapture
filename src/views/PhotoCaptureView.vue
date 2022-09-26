<template>
    <div class="about">
      <h1>Capture an image of your t-shirt</h1>
      <camera :resolution="{ width: 375, height: 812 }" autoplay></camera>
    </div>
  </template>
  
  <style>
  @media (min-width: 1024px) {
    .about {
      min-height: 100vh;
      display: flex;
      align-items: center;
    }
  }
  </style>

  <script>
    import Camera from "simple-vue-camera";

    //inside your vue options api
    export default {
        components: {
          Camera,
        },
        mounted() {
          console.log('mounted')
        }
    }
  </script>