<template>
  <span class="go-back">
    <button @click="goBack">Go Back</button>
  </span>
</template>

<script>
export default {
  name: "GoBack",
  methods: {
    goBack() {
      return this.$router.go(-1)
    },
  },
}
</script>

<style lang="scss" scoped>
.go-back {
  display: flex;
  padding-left: 30px;
  button {
    /*     --color: #7d7d7d;
    --l: 50%;
    --color-darker: hsl(var(--color), calc(var(--l) - 5%)); */
    border: none;
    padding: 0.5rem;
    border-radius: 4px;
    color: #fff;
    background: var(--color-primary-darker);
    cursor: pointer;
    transition: background 0.25s cubic-bezier(0.075, 0.82, 0.165, 1);
    &:hover {
      background: var(--color-primary-darkest);
    }
  }
}
</style>
