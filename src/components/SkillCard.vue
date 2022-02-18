<template>
  <div class="skill-card--container">
    <div class="skill-card--icon-block">
      <Icon :icon="icon" class="skill-card--icon" />
    </div>
    <div class="skill-card--text-block">
      <span>{{ text }}</span>
    </div>
  </div>
</template>

<script>
import { Icon } from "@iconify/vue2"
export default {
  name: "SkillCard",
  components: {
    Icon,
  },
  props: {
    icon: {
      type: String,
      require: true,
    },
    text: {
      type: String,
      require: true,
    },
  },
}
</script>

<style lang="scss" scoped>
.skill-card--container {
  color: #82868b;
  background-color: #fbfbfc;
  padding: 30px 10px 20px 10px;
  width: 160px;
  border-style: solid;
  border-color: #cdcdce;
  border-width: 2px;
  border-radius: 6px;
  margin-right: 10px;
  &:hover {
    color: #568be4;
    border-color: #568be4;
  }
}

.skill-card--icon-block {
  display: flex;
  justify-content: center;
}

.skill-card--icon {
  font-size: 2rem;
  text-align: center;
}

.skill-card--text-block {
  display: flex;
  justify-content: center;
  margin-top: 1.5rem;
  font-weight: 500;
  font-size: 0.7rem;
}

// Small devices (landscape phones, 576px and up)
@media screen and (min-width: 576px) {
}

// Medium devices (tablets, 768px and up)
@media screen and (min-width: 768px) {
}

// Large devices (desktops, 992px and up)
@media screen and (min-width: 992px) {
  .skill-card--icon {
    font-size: 4rem;
    text-align: center;
  }
  .skill-card--text-block {
    font-size: 1.15rem;
  }
  .skill-card--container {
    margin-right: 60px;
  }
}

// Extra large devices (large desktops, 1200px and up)
@media screen and (min-width: 1200px) {
}
</style>
