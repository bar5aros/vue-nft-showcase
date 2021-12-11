<template>
  <main class="showcase-area">
    <BSearchbar @search="searchNft" :searched="searched"/>
    <div class="centered">
      <section v-if="isFiltered" class="card-layout">
        <BCard v-for="nft in filteredNfts" :key="nft.token_id" :nft="nft"/>
      </section>
      <section v-if="!isFiltered" class="card-layout">
        <BCard v-for="nft in nfts" :key="nft.token_id" :nft="nft"/>
      </section>
    </div>
  </main>
</template>

<script>
import BCard from "@/components/BCard";
import BSearchbar from "@/components/BSearchbar";

export default {
  name: "Showcase",
  components: {
    BCard,
    BSearchbar,
  },
  data() {
    return {
      nfts: [],
      errors: [],
      filteredNfts: [],
      searched: '',
      isFiltered: false,
    };
  },
  beforeMount() {
    this.fetchNFTs();
    console.log(this.isFiltered);
  },
  methods: {
    async fetchNFTs() {
      try {
        const {
          data: {data, status},
        } = await this.$axios.get("/");
        console.info(data, status);
        this.nfts = data;
      } catch (error) {
        this.errors.push(error);
      }
    },
    searchNft(query) {
      if (query.length > 0) {
        this.isFiltered = true;
        this.searched = query;
        this.filteredNfts = this.nfts.filter(nft => {
          return nft.name.toLowerCase().includes(query.toLowerCase());
        });
      } else {
        this.isFiltered = false;
        this.searched = '';
      }
    }
  },
};
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
