<template>
  <div
    class="base-buton--container base-button--outline-style"
    @click="linkToToDoPage()"
  >
    <span
      >To Do Page
      <Icon icon="heroicons-outline:paper-airplane" class="base-buton--icon" />
    </span>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue2"
export default {
  name: "BaseButton",
  components: {
    Icon,
  },
  methods: {
    linkToToDoPage() {
      if (this.$router.currentRoute.path != "/to-do-page") {
        this.$router.push("/to-do-page")
      }
    },
  },
}
</script>

<style lang="scss" scoped>
.base-buton--container {
  background-color: #568be4;
  font-size: 0.8rem;
  font-weight: 500;
  display: flex;
  padding: 0.5rem 0.8rem;
  border-radius: 20px;
  &:hover {
    cursor: pointer;
  }
}

.base-button--outline-style {
  border-style: solid;
  border-width: 1px;
  border-color: #568be4;
  color: white;
  &:hover {
    background-color: #3778c2;
  }
}

.base-buton--icon {
  margin-left: 3px;
  padding-bottom: 2px;
  font-size: 18px;
  display: inline;
  transform: rotate(45deg);
}
</style>
