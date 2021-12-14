<template>
  <div class="page-container">
    <div>
      <countdown :end-date="new Date('2021/12/15')" />

      <ul class="offer-items-wrapper">
        <OfferItem
          v-for="offer in offers"
          :key="offer.id"
          :offer="offer"
          :selected-price="selectedPrice"
          @offerSelect="handleOfferSelect"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import OfferItem from "./OfferItem.vue";
import Countdown from "~/components/Countdown.vue";

export default {
  components: {
    OfferItem,
    Countdown,
  },
  data() {
    return {
      picked: false,
      selectedPrice: null,
      offers: [],
    };
  },
  mounted() {
    this.offers = Array.from(Array(5).keys()).map((i) => ({
      id: `offer-${i}`,
      name: `${24 + i}-hour Hop-on Hop-off City Tour Ticket`,
      originalPrice: `$${Math.floor(Math.random() * 50 + 50)}`,
      discountedPrice: `$${Math.floor(Math.random() * 50 + 50)}`,
      discount: `${Math.floor(Math.random() * 10 + 5)}%`,
      numBought: Math.floor(Math.random() * 50 + 90),
    }));
    this.selectedPrice = this.offers[0];
  },
  methods: {
    handleOfferSelect(offer) {
      this.selectedPrice = offer;
    },
  },
};
</script>

<style>
.page-container {
  width: 100vw;
  height: 100vh;
  background-color: #eee;
  display: flex;
  align-items: center;
  justify-content: center;
}

.offer-items-wrapper {
  width: 500px;
  background-color: white;
}
</style>
