<template>
  <div id="app">
    <TheNavigation />
    <transition name="slide" mode="out-in">
      <router-view :key="$route.path"></router-view>
    </transition>
  </div>
</template>

<script>
import TheNavigation from "./components/TheNavigation.vue"
export default {
  components: { TheNavigation },
}
</script>

<style lang="scss" scoped></style>
<style lang="scss">
.slideUp-enter-active,
.slideUp-leave-active {
  transition: opacity 0.25s cubic-bezier(0.175, 0.885, 0.32, 1.275),
    transform 0.25s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.slideUp-enter,
.slideUp-leave-to {
  opacity: 0;
  transform: translateY(-30px);
}
.slide-enter-active,
.slide-leave-active {
  transition: opacity 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275),
    transform 0.5s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}
.slide-enter,
.slide-leave-to {
  opacity: 0;
  transform: translateX(-30px);
}
:root {
  --color: 180, 0%;
  --l: 50%;
  --color-primary: hsl(var(--color), var(--l));
  --color-primary-darker: hsl(var(--color), calc(var(--l) - 5%));
  --color-primary-darkest: hsl(var(--color), calc(var(--l) - 10%));
  --color-darker: hsl(bisque);
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
