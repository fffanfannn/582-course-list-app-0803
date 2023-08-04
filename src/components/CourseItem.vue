<template>
  <div class="course-card" :class="{ isFull, isSelected }">
    <p>Course: {{ given.courseName }}</p>
    <p>Discription: {{ given.courseDiscription }}</p>
    <ul>
      <li>Credit: {{ given.courseCredit }}</li>
      <li>Hours: {{ given.courseHour }}</li>
      <li>Student number: {{ given.studentNum + count }} /20</li>
      <li>
        ENROLLMENT: {{ given.studentNum }},
        <span class="status">{{ enrollmentStatus }}</span>
      </li>
      <!-- <li v-if="given.studentNum + count < 20">Status: Available</li>
      <li v-else>Status: Not available</li> -->
    </ul>
    <!-- <div v-if="given.studentNum + count < 20"> -->
    <button
      :class="av"
      v-if="!isSelected && given.studentNum < 20"
      @click="courseAdd"
    >
      Add Course
    </button>
    <button
      :class="nav"
      v-else-if="isSelected && given.studentNum < 20"
      @click="courseRemove"
    >
      Remove Course
    </button>
    <!-- <button @click="outerAdd">Add to parent</button> -->
    <!-- </div> -->
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
      selectedbg: "selected-bg",
      isSelected: false,
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
      // this.count++;
      this.isSelected = true;
      this.$emit("count-to-parent");
      this.$emit("selected-course-display", this.given);
    },

    courseRemove() {
      // this.count--;
      this.isSelected = false;
      this.$emit("count-remove-parent");
    },

    // outerAdd() {
    //   this.$emit("count-to-parent");
    // },
  },

  computed: {
    enrollmentStatus() {
      if (this.given.studentNum == 0) {
        return "empty";
      } else if (this.given.studentNum >= 20) {
        return "full";
      } else {
        return "available to join";
      }
    },
    isFull() {
      return this.given.studentNum >= 20;
    },
  },
};
</script>

<style scope lang="scss">
.av-label {
  border: 1px solid transparent;
  background-color: rgb(0, 128, 107);
  font-size: 1rem;
  padding: 5px 10px;
  color: white;
  font-weight: 600;
  letter-spacing: 0.1rem;
  display: inline-block;
}

.av-label.disable {
  border: 1px solid rgb(6, 67, 77);
  background-color: transparent;
  color: rgb(6, 67, 77);
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

.isFull {
  color: rgb(204, 204, 204);
}

.isSelected {
  background-color: rgb(203, 237, 240);
}
</style>
