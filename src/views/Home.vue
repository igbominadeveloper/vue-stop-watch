<template>
  <main>
    <app-title title="Stop Watch" />
    <app-timer>
      <template #control="{ clickHandler, startTime }">
        <app-button @click="clickHandler">
          {{ startTime > 0 ? 'Stop' : 'Start' }}
        </app-button>
      </template>
    </app-timer>
  </main>
</template>

<script>
import AppTitle from '@components/Title.vue';
import AppButton from '@components/Button.vue';
import AppTimer from '@components/Timer.vue';

export default {
  name: 'Home',
  components: {
    AppTitle,
    AppButton,
    AppTimer,
  },
};
</script>

<style scoped>
main {
  width: 100%;
  height: 100%;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;

  background-color: var(--color-primary-gray);
}
</style>
