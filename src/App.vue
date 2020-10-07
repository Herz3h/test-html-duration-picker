<template>
  <div id="app">
    <input :value="formatDuration(substep.estimatedDuration)"
      @input="substep.estimatedDuration = durationToMinutes($event.target.value)"
      class="form-control html-duration-picker" data-hide-seconds />

  </div>
</template>

<script>
/* eslint-disable no-debugger */
import * as HtmlDurationPicker from 'html-duration-picker'

export default {
  name: 'App',
  data()
  {
    return {
      substep: {
        estimatedDuration: 100
      }
    };
  },
  mounted()
  {
    HtmlDurationPicker.init();
  },
  methods:
  {
    formatDuration(duration)
    {
      if (typeof duration==='number' && (duration%1)===0)
      {
        const hours = parseInt(duration / 60);
        const minutes = duration % 60;
        const result = hours.toString().padStart(2, '0') + ":" + minutes.toString().padStart(2, '0');
        debugger
        return result;
      }
    },

    durationToMinutes(duration)
    {
      const split = duration.split(':');
      const minutes = Number(split[1]);
      const hoursToMinutes = Number(split[0]) * 60;
      return hoursToMinutes + minutes;
    },

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
