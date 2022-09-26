<template>
    <div class="about">
      <h1>Capture an image of your t-shirt</h1>
      <h1>{{ url }}</h1>
      <camera :resolution="{ width: 375, height: 812 }" autoplay></camera>
      <button @click="snapshot">Create snapshot</button>
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

  <script lang="ts">
    import Camera from "simple-vue-camera";
    import { ref, defineComponent } from 'vue';

    //inside your vue options api
    export default defineComponent({
      data() {
        return {
          blobUrl: '',
        }
      },
      components: {
          Camera,
        },
        setup() {
        // Get a reference of the component
  
        const camera = ref<InstanceType<typeof Camera>>();
        
        var url = ""
        // Use camera reference to call functions
        const snapshot = async () => {
            const blob = await camera.value?.snapshot() as Blob;

            // To show the screenshot with an image tag, create a url
            url = URL.createObjectURL(blob);
        }

        return {
            camera,
            snapshot,
            url
        }
        },
        mounted() {
          console.log('mounted')
        }
    });
  </script>