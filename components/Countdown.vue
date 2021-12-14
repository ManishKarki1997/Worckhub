<template>
  <div class="countdown">
    <div class="timer-wrapper" v-if="formattedTimer">
      <p class="timer-info">Sale ends in</p>
      <div class="timer">
        <p>{{ formattedTimer.hours }}:</p>
        <p>{{ formattedTimer.minutes }}:</p>
        <p>{{ formattedTimer.seconds }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    endDate: {
      type: Date,
      default: new Date("2021/12/15"),
    },
  },
  data() {
    return {
      now: new Date(),
      timeInSeconds: 500,
      intervalRef: null,
    };
  },
  computed: {
    formattedTimer() {
      const h = Math.trunc((this.endDate - this.now) / 1000 / 3600);
      const formattedHours = h > 0 ? h : `0${h}`;

      const min = Math.trunc((this.endDate - this.now) / 1000 / 60) % 60;
      const formattedMins = min > 9 ? min : `0${min}`;

      const secs = Math.trunc((this.endDate - this.now) / 1000) % 60;
      const formattedSeconds = secs > 9 ? secs : `0${secs}`;

      return {
        hours: formattedHours,
        minutes: formattedMins,
        seconds: formattedSeconds,
      };
    },
  },

  mounted() {
    this.intervalRef = setInterval(() => {
      this.now = new Date();
    }, 1000);
  },
  beforeDestroy() {
    clearInterval(this.intervalRef);
  },
};
</script>

<style scoped>
.countdown {
  margin-bottom: 8px;
}
.timer-wrapper,
.timer {
  display: flex;
  align-items: center;
}

.timer-wrapper .timer-info {
  margin-right: 4px;
}
.timer {
  color: red;
  font-weight: 500;
}
</style>
