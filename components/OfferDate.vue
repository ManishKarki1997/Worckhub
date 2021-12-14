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
      maxDays: 10,
      selectedDateRange: {
        start: new Date("2021/12/14"),
        end: new Date("2021/12/16"),
      },
      dateAttributes: [
        {
          dates: new Date("2021/12/25"),
          popover: {
            label: "Game at PSG",
          },
        },
        {
          dates: new Date("2021/12/30"),
          popover: {
            label: "Game at Bernabeu",
          },
        },
      ],
    };
  },
  watch: {
    selectedDateRange: {
      immediate: true,
      deep: true,
      handler(range) {
        if (range.start && range.end) {
          const dateDiff = range.end - range.start;
          const totalDays = Math.ceil(dateDiff / (1000 * 60 * 60 * 24));

          this.dateAttributes = Array.from(Array(totalDays).keys()).map(
            (i, idx) => {
              const d = new Date(range.start);
              d.setDate(d.getDate() + idx);

              return {
                dates: new Date(d),

                popover: {
                  label: `Rs. ${Math.floor(Math.random() * 1050 + 1900)}`,
                },
              };
            }
          );

          // include the checkout text for the last date
          this.dateAttributes.push({
            dates: range.end,

            popover: {
              label: `Checkout Rs. ${Math.floor(Math.random() * 1250 + 2100)}`,
            },
          });
        }
      },
    },
  },
};
</script>

<style></style>
