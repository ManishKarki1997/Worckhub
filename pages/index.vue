<template>
  <div>
    <package-offer />
  </div>
</template>

<script>
import PackageOffer from "~/components/PackageOffer.vue";
export default {
  components: {
    PackageOffer,
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}
</style>
