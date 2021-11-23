<template>
  <main class="showcase-area">
    <div class="centered">
      <section class="card-layout">
        <Card v-for="nft in nfts" :key="nft.token_id" :nft="nft"/>
      </section>
    </div>
  </main>
</template>

<script>
import Card from "@/components/Card";

export default {
  name: 'Showcase',
  components: {
    Card
  },
  data() {
    return {
      nfts: [],
      errors: []
    }
  },
  beforeMount() {
    this.fetchNFTs();
  },
  methods: {
    async fetchNFTs() {
      try {
        const {data: {data, status}} = await this.$axios.get("/");
        console.info(data, status);
        this.nfts = data;
      } catch (error) {
        this.errors.push(error);
      }
    },
  }
}
</script>

<style scoped>
.centered {
  margin: 0 auto;
  padding: 0 1em;
}

.card-layout {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  align-content: space-around;
  margin: 0 auto;
  padding: 0 0.5em;
}
</style>
