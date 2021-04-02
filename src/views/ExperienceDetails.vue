<template>
  <section class="experience">
    <h1>Experiences</h1>
    <h2>{{ experience.name }}</h2>
    <div class="experience-details">
      <img
        :src="require(`@/assets/${experience.image}`)"
        :alt="experience.name"
      />
      <p>
        {{ experience.description }}
      </p>
    </div>
  </section>
  <!-- <transition name="slideUp">
  </transition> -->
</template>

<script>
import store from "@/store.js"
export default {
  name: "ExperienceDetails",
  props: {
    slug: {
      type: String,
      required: true,
    },
    experienceSlug: {
      type: String,
      required: true,
    },
  },
  data() {
    return {}
  },
  computed: {
    destination() {
      return store.destinations.find(
        (destination) => destination.slug == this.slug
      )
    },
    experience() {
      return this.destination.experiences.find(
        (experience) => experience.slug == this.experienceSlug
      )
    },
  },
}
</script>

<style lang="scss" scoped>
.experience {
  width: 97%;
  margin: 0 auto;
  .experience-details {
    img {
      max-width: 600px;
      height: auto;
      width: 100%;
      min-height: 400px;
    }
    display: flex;
    justify-content: space-between;
    p {
      margin: 0 40px;
      font-size: 20px;
      text-align: left;
    }
  }
}
</style>
