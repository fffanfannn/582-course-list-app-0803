<template>
  <div :class="courseCard">
    <p>Course: {{ given.courseName }}</p>
    <p>Credit: {{ given.courseCredit }}</p>
    <p>Hours: {{ given.courseHour }}</p>
    <p>Discription: {{ given.courseDiscription }}</p>
    <p>Student number: {{ given.studentNum + count }} /20</p>
    <p v-if="given.studentNum + count < 20">Status: Available</p>
    <p v-else>Status: Not available</p>
    <div v-if="given.studentNum + count < 20">
      <button :class="av" v-if="selected" @click="innerAdd">Add</button>
      <button :class="nav" v-else>Cancel</button>
      <!-- <button @click="outerAdd">Add to parent</button> -->
    </div>
  </div>
</template>

<script>
export default {
  name: "CourseItem",

  data() {
    return {
      count: 0,
      av: "av-label",
      nav: "av-label disable",
      courseCard: "course-card",
      selected: true,
    };
  },

  props: {
    given: {
      type: Object,
      required: true,
    },
  },

  methods: {
    innerAdd() {
      this.count++;
      this.$emit("count-to-parent");
      this.selected = !this.selected;
    },
    outerAdd() {
      this.$emit("count-to-parent");
    },
  },
};
</script>

<style>
.av-label {
  border: 1px solid red;
}

.av-label.disable {
  border: 1px solid rgb(0, 255, 64);
}

.course-card {
  border: 1px solid darkgray;
  width: 600px;
  padding: 1.5rem;
  text-align: left;
  margin-bottom: 2rem;
}
</style>
