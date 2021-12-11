<template>
  <div id="Searchbar">
    <b-form-input v-model="search" placeholder="Search an NFT" @input="sendSearch"></b-form-input>
    <div class="mt-2">Searched NFT: {{ searched }}</div>
  </div>
</template>
<script>
export default {
  name: "BSearchbar",
  props: {
    searched: {
      type: String,
      default: ""
    }
  },
  data() {
    return {
      search: '',
    }
  },
  methods: {
    sendSearch(){
      this.$emit('search', this.search)
    }
  }
}
</script>

<style>

</style>
