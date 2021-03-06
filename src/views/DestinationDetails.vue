<template>
  <div>
    <GoBack />
    <section class="destination">
      <h1>{{ destination.name }}</h1>
      <div class="destination-details">
        <img
          :src="require(`@/assets/${destination.image}`)"
          :alt="destination.name"
        />
        <p>
          {{ destination.description }}
        </p>
      </div>
    </section>
    <section class="experineces">
      <h2>Top experiences in {{ destination.name }}</h2>
      <div class="cards">
        <div
          class="card"
          v-for="experience in destination.experiences"
          :key="experience.slug"
        >
          <router-link
            :to="{
              name: 'experienceDetails',
              params: { experienceSlug: experience.slug },
            }"
          >
            <img
              :src="require(`@/assets/${experience.image}`)"
              :alt="experience.name"
            />
            <span class="card__text">
              {{ experience.name }}
            </span>
          </router-link>
        </div>
      </div>
      <router-view :key="$route.path" v-slot="{ Component }" appear>
        <transition :name="transitionName">
          <component :is="Component" />
        </transition>
      </router-view>
    </section>
  </div>
</template>

<script>
import store from "@/store.js"

import GoBack from "@/components/GoBack"

export default {
  name: "DestinationDetails",
  props: {
    slug: {
      type: String,
      required: true,
    },
  },
  components: { GoBack },
  data() {
    return {
      transitionName: "slideUp",
    }
  },
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug == this.slug
      )
    },
  },
  beforeRouteUpdate(to, from, next) {
    const toDepth = to.path.split("/").length
    const fromDepth = from.path.split("/").length
    this.transitionName = toDepth < fromDepth ? "slideUp" : "slideUp"
    next()
  },
}
</script>

<style lang="scss" scoped>
.destination {
  width: 97%;
  margin: 0 auto;
}
img {
  max-width: 600px;
  height: auto;
  width: 100%;
  min-height: 400px;
}
.destination-details {
  display: flex;
  justify-content: space-between;
}
p {
  margin: 0 40px;
  font-size: 20px;
  text-align: left;
}
.cards {
  display: flex;
  justify-content: space-between;
  .card {
    padding: 0 20px;
    position: relative;
    img {
      max-height: 200px;
      min-height: unset;
    }
    &__text {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
      color: #fff;
      font-size: 1.5rem;
      font-weight: bold;
      text-decoration: none;
    }
  }
}
</style>
