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
      <button :class="av" v-if="selected" @click="courseAdd">Add Course</button>
      <button :class="nav" v-else @click="courseRemove">Selected</button>
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
    courseAdd() {
      this.count++;
      this.$emit("count-to-parent");
      this.selected = !this.selected;
      this.$emit("selected-course-display", this.given);
    },

    courseRemove() {
      this.count--;
      this.$emit("count-remove-parent");
      this.selected = !this.selected;
    },
    // outerAdd() {
    //   this.$emit("count-to-parent");
    // },
  },
};
</script>

<style>
.av-label {
  border: 1px solid transparent;
  background-color: rgb(0, 128, 107);
  font-size: 1rem;
  padding: 5px 10px;
  color: white;
  font-weight: 600;
  letter-spacing: 0.1rem;
}

.av-label.disable {
  background-color: rgb(6, 67, 77);
  color: white;
}

.course-card {
  border: 1px solid rgb(211, 211, 211);
  width: 400px;
  padding: 1.5rem;
  text-align: left;
  margin-bottom: 2rem;
  box-shadow: 0 4px 8px 0 rgba(63, 63, 63, 0.2),
    0 6px 20px 0 rgba(77, 77, 77, 0.19);
}
</style>
