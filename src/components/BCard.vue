<template>
  <div
    class="card"
    v-b-hover="handleCardHover"
    :style="isHovered ? hoveredStyle : {}"
  >
    <b-card
      no-body
      title="Fluffy Polar Bears 99 Special Edition#2"
      img-alt="NFT"
      img-top
      tag="article"
      style="
        max-width: 15rem;
        background: #fff;
        box-sizing: border-box;
        margin: 0 1em;
      "
    >
      <b-img-lazy :src="nftImage" alt="NFT"></b-img-lazy>
      <b-card-body>
        <b-card-text style="font-family: 'Outfit', Arial, sans-serif">{{
          nftName
        }}</b-card-text>
        <b-card-text style="font-family: 'M PLUS 2', Arial, sans-serif">
          Price: {{ ethPrice }}
          <font-awesome-icon icon="fab fa-ethereum" />
          ($ {{ dollarPrice }})
        </b-card-text>
      </b-card-body>
      <b-card-footer style="text-align: end; background: #fff">
        <button v-on:click="handleFavorite">
          <font-awesome-icon
            icon="fa-solid fa-heart"
            v-if="isFavorite"
            class="favorite-icon"
          />
          <font-awesome-icon
            icon="fa-regular fa-heart"
            v-else
            class="favorite-icon"
          />
        </button>
      </b-card-footer>
    </b-card>
  </div>
</template>

<script>
import { library } from "@fortawesome/fontawesome-svg-core";
import { faEthereum } from "@fortawesome/free-brands-svg-icons";
import { faHeart } from "@fortawesome/free-solid-svg-icons";
import { faHeart as faHeartRegular } from "@fortawesome/free-regular-svg-icons";

library.add(faEthereum, faHeart, faHeartRegular);

export default {
  name: "Card",
  props: {
    nft: Object,
  },
  data() {
    return {
      isHovered: false,
      isFavorite: false,
      hoveredStyle: {
        background: "#f5f5f5",
        border: "1px solid #e3e3e3",
        boxShadow: "0 0.5rem 1rem rgba(0, 0, 0, 0.15)",
        cursor: "pointer",
        transition: "all 0.2s ease-in-out",
      },
    };
  },
  computed: {
    nftImage() {
      return this.nft.image_thumbnail_url;
    },
    nftName() {
      return this.nft.name;
    },
    ethPrice() {
      return this.nft.collection.payment_tokens[0].eth_price;
    },
    dollarPrice() {
      return this.nft.collection.payment_tokens[0].usd_price;
    },
  },

  methods: {
    handleCardHover(hovered) {
      this.isHovered = hovered;
    },
    handleFavorite() {
      this.isFavorite = !this.isFavorite;
    },
  },
};
</script>

<style>
.card {
  margin: 15px;
  border-radius: 0.5rem;
}

article.card {
  margin: 0 !important;
}

button {
  border: none;
  background: transparent;
  padding: 0;
  margin: 0;
}

button:focus {
  outline: none;
  box-shadow: none;
}

.favorite-icon {
  color: darkred;
}
</style>
