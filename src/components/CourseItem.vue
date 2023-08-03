<template>
  <div>Course Name</div>
  <p>Name: {{ given.courseName }}</p>
  <!-- <p>Credit: {{ given.courseCredit }}</p>
  <p>Hours: {{ given.courseHour }}</p>
  <p>Discription: {{ given.courseDiscription }}</p> -->
  <p>Student number: {{ given.studentNum + count }}</p>
  <p>{{ count }} /20</p>
  <p>Location:</p>

  <button :class="av" v-if="selected" @click="innerAdd">Add</button>
  <button :class="nav" v-else>Cancel</button>
  <!-- <button @click="outerAdd">Add to parent</button> -->
</template>

<script>
export default {
  name: "CourseItem",

  data() {
    return {
      count: 0,
      av: "av-label",
      nav: "av-label disable",
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
</style>
