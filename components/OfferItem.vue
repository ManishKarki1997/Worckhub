<template>
  <li class="offer-item">
    <div class="radio-btn">
      <input
        @change="handleOfferChecked"
        type="radio"
        id="offer-price"
        value="One"
        :name="offer.id"
        :checked="selectedPrice.id === offer.id"
      />
    </div>

    <label @click="handleOfferChecked" :for="offer.id">
      <div class="offer-info-wrapper">
        <h4 class="offer-name">{{ offer.name }}</h4>

        <div class="price-wrapper">
          <h4 class="original-price">{{ offer.originalPrice }}</h4>
          <h4 class="discounted-price">{{ offer.discountedPrice }}</h4>
          <p class="discount">{{ offer.discount }} off</p>
        </div>

        <div class="number-bought">
          <p>{{ offer.numBought }}+ bought</p>
        </div>
      </div>
    </label>
  </li>
</template>

<script>
export default {
  props: {
    offer: {
      type: Object,
      required: true,
    },
    selectedPrice: {
      type: Object,
      required: true,
    },
  },
  methods: {
    handleOfferChecked() {
      this.$emit("offerSelect", this.offer);
    },
  },
};
</script>

<style scoped>
.offer-item {
  width: 100%;
  display: flex;
  padding: 12px;
  border-bottom: 1px solid rgba(128, 128, 128, 0.24);
}

.offer-item .radio-btn {
  width: 40px;
  max-width: 40px;
  margin-top: 3px;
}
.radio-btn input {
  width: 20px;
  height: 20px;
}

.offer-item label {
  width: 100%;
}

.offer-info-wrapper {
  margin-left: 8px;
}

.offer-info-wrapper .offer-name {
  font-weight: 500;
  margin-bottom: 10px;
}

.offer-info-wrapper .price-wrapper {
  display: flex;
  align-items: center;
  font-size: 1.2rem;
  margin-bottom: 10px;
}

.price-wrapper > * {
  margin-right: 12px;
}

.price-wrapper .original-price {
  font-weight: 300;
  text-decoration: line-through;
}

.price-wrapper .discounted-price {
  color: green;
}

.price-wrapper .discount {
  background-color: rgba(0, 128, 0, 0.192);
  color: green;
  font-size: 0.8rem;
  font-weight: 500;
  border-radius: 5px;
  padding: 2px 4px;
}

.offer-item .number-bought {
  color: rgb(109, 107, 107);
  font-size: 0.9rem;
}
</style>
