<template>
  <vc-date-picker
    :attributes="dateAttributes"
    :min-date="new Date()"
    v-model="selectedDateRange"
    is-range
  />
</template>

<script>
export default {
  data() {
    return {
      selectedDateRange: {
        start: new Date("2021/12/14"),
        end: new Date("2021/12/16"),
      },
      dateAttributes: [
        {
          dates: new Date("2021/12/25"),
          dot: "blue",
          popover: {
            label: "Game at PSG",
          },
        },
        {
          dates: new Date("2021/12/30"),
          dot: "blue",
          popover: {
            label: "Game at Bernabeu",
          },
        },
      ],
    };
  },
};
</script>

<style></style>
