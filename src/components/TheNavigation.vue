<template>
  <div id="nav">
    <p class="logo">Vue Router for Everyone Practice App</p>
    <ul class="nav-links">
      <li class="links">
        <router-link to="/"> Home </router-link>
      </li>
      <li
        v-for="destination in destinations"
        :key="destination.name"
        class="links"
      >
        <router-link
          :to="{
            name: 'DestinationDetails',
            params: { slug: destination.slug },
          }"
        >
          {{ destination.name }}
        </router-link>
      </li>
    </ul>
  </div>
</template>

<script>
import store from "@/store"
export default {
  name: "TheNavigation",
  data() {
    return {
      destinations: store.destinations,
    }
  },
}
</script>

<style lang="scss" scoped>
#nav {
  padding: 1rem 1.5rem;
  display: flex;
  align-items: center;
  position: sticky;
  top: 0;
  background: #fff;
  z-index: 1;
  border-bottom: 2px solid var(--color-primary-darkest);
  margin-bottom: 1rem;

  a {
    font-weight: bold;
    color: #2c3e50;
    padding: 0 10px;
    text-decoration: none;
    font-weight: bold;

    &.router-link-exact-active {
      color: #42b983;
    }
    &.router-exact-active {
      color: #42b983;
    }
  }

  .nav-links {
    display: flex;
    .links {
      padding-right: 20px;
      list-style: none;
      &:hover {
        text-decoration: underline;
      }
    }
  }
  .logo {
    font-size: 1.5rem;
    font-weight: bold;
    margin: 0;
  }
}
</style>
