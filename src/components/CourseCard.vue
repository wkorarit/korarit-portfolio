<template>
    <div class="course-card--container">
      <span>{{ text }}</span>
    </div>
</template>

<script>
export default {
  name: "CourseCard",
  props: {
    text: {
      type: String,
      require: true,
    },
  },
}
</script>

<style lang="scss" scoped>

.course-card--container {
  background-color: #fbfbfc;
  border: 1px solid #ecedee;
  border-radius: 6px;
  padding: 2rem 1.5rem;
  margin-right: 20px;
  margin-bottom: 20px;
  font-size: 0.85rem;
  &:hover {
    color: #7367f0;
    background-color: #f7f6fe;
    border: 1px solid #7367f0;
  }
}

@media screen and (min-width: 768px) {
  .course-card--container {
    font-size: 1rem
}

}
</style>
