<template>
  <div class="timer">
    <div class="timer-body">
      {{ time }}
    </div>

    <div class="timer-footer">
      <slot name="control" :clickHandler="handleClick" :startTime="startTime" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Timer',

  data: () => ({
    startTime: 0,
    interval: null,
    time: '00:00:00',
  }),

  methods: {
    handleClick() {
      if (this.startTime > 0) {
        this.stopTimer();
        return;
      }

      this.startTimer();
    },

    startTimer() {
      this.stopTimer();

      this.interval = setInterval(() => {
        this.startTime += 1;
        this.time = this.formatTime(this.startTime);
      }, 10);
    },

    stopTimer() {
      clearInterval(this.interval);
      this.startTime = 0;
      this.time = '00:00:00';
    },

    padTimeWithZero(time) {
      return time.toString().padStart(2, '0');
    },

    formatTime(time) {
      const minutes = Math.floor(time / 6000);

      const seconds = Math.floor((time / 100) % 60);

      const hundreds = Math.floor(time % 100);

      const minuteString = this.padTimeWithZero(minutes);
      const secondsString = this.padTimeWithZero(seconds);
      const hundredthsString = this.padTimeWithZero(hundreds);

      return `${minuteString}:${secondsString}:${hundredthsString}`;
    },
  },
};
</script>

<style scoped>
.timer {
  display: flex;
  flex-direction: column;
  gap: 20px;
  align-items: center;
}

.timer-body {
  border: 0.5px solid var(--color-secondary-black);
  padding: 15px;
  border-radius: 20px;
  font-size: 2em;
}

.timer-footer {
  width: 100%;

  display: flex;
  justify-content: center;

}
</style>
