<template>
  <div class="navbar--container">
    <div class="navbar--name" @click="linkToHome()"><span>KORARIT.</span></div>
    <div class="navbar--todo-button"><base-button></base-button></div>
  </div>
</template>

<script>
import BaseButton from "./BaseButton"
export default {
  components: { BaseButton },
  name: "Navbar",
  methods: {
    linkToHome() {
      if (this.$router.currentRoute.path != "/") {
        this.$router.push("/")
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.navbar--container {
  z-index: 10;
  display: flex;
  justify-content: space-between;
  width: 100%;
  padding: 1rem 2rem;
  position: fixed;
  background-color: #3e4c59;
}

.navbar--name {
  font-weight: 600;
  display: flex;
  color: white;
  align-self: center;
  &:hover {
    cursor: pointer;
  }
}

.navbar--todo-button {
  display: flex;
}

// Small devices (landscape phones, 576px and up)
@media screen and (min-width: 576px) {
}

// Medium devices (tablets, 768px and up)
@media screen and (min-width: 768px) {
}

// Large devices (desktops, 992px and up)
@media screen and (min-width: 992px) {
  .navbar--container {
    padding: 0.5rem 20rem;
  }
}

// Extra large devices (large desktops, 1200px and up)
@media screen and (min-width: 1200px) {
  .navbar--container {
    padding: 0.5rem 29rem;
  }
}
</style>
