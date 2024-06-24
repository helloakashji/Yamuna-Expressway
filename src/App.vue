<template>
     <!-- <Spinner v-if="isLoading" /> -->
    <!-- Your main application content -->
    <router-view />
</template>

<script>
// import Spinner from './views/utilities/Spinner.vue';
export default {
    components: {
    //   Spinner
    },
    data() {
      return {
        isLoading: true // Set to true initially to show the spinner
      };
    },
    mounted() {
      // Simulate an asynchronous action (e.g., fetching data)
      setTimeout(() => {
        this.isLoading = false; // Set to false when loading is complete
      }, 3000); // Simulating a 3-second loading time
    }
  };
  </script>
