<template>
  <header class="masthead clear">
    <div class="centered">
      <div class="site-branding">
        <h1 class="site-title">NFT Showcase</h1>
      </div>
      <!-- .site-title -->
    </div>
    <!-- .centered -->
  </header>
</template>

<script>
export default {
  name: "Header",
  data() {
    return {
      title: "Vue.js",
    };
  },
};
</script>

<style scoped>
.masthead {
  background-color: #264653;
}

.site-title {
  color: white;
  font-size: 3rem;
  font-family: "Outfit", Arial, sans-serif;
}
</style>
