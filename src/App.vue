<template>
  <div id="app">
    <InputText />
  </div>
</template>

<script>
import InputText from '@/components/InputText.vue';

export default {
  name: 'App',
  components: {
    InputText,
  },
};
</script>

<style>
* {
  padding: 0;
  margin: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  background: antiquewhite;
  min-height: 100vh;
  width: 100vw;
  display: flex;
  justify-content: center;
}
</style>
