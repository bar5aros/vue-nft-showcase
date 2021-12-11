<template>
  <div id="app">
    <b-header />
    <b-showcase />
  </div>
</template>

<script>
import BHeader from "@/components/BHeader";
import BShowcase from "@/components/BShowcase";
import BSearchbar from "@/components/BSearchbar";

export default {
  name: "App",
  components: {
    BHeader,
    BShowcase,
  },
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Outfit:wght@500&display=swap");
@import url("https://fonts.googleapis.com/css2?family=M+PLUS+2:wght@500&family=Outfit:wght@500&family=Rubik&display=swap");

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
