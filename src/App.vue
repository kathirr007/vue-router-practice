<template>
  <div id="app">
    <the-navigation />
    <router-view :key="$route.path" />
  </div>
</template>

<script>
import TheNavigation from "./components/TheNavigation.vue"
export default {
  components: { TheNavigation },
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
<style lang="css">
:root {
  --color: 180, 0%;
  --l: 50%;
  --color-primary: hsl(var(--color), var(--l));
  --color-primary-darker: hsl(var(--color), calc(var(--l) - 5%));
  --color-primary-darkest: hsl(var(--color), calc(var(--l) - 10%));
  --color-darker: hsl(bisque);
}
</style>
