<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  <h1>Vue Course List</h1>
  <h2>Course selected: {{ count }}</h2>
  <div :class="courseFlexbox">
    <CourseItem
      v-for="courseList in courseLists"
      :key="courseList.id"
      :given="courseList"
      @count-to-parent="addOne"
    />
  </div>

  <div :class="mySelection">

  </div>
</template>

<script>
// import HelloWorld from "./components/HelloWorld.vue";
import CourseItem from "./components/CourseItem.vue";

export default {
  name: "App",

  components: {
    CourseItem,
  },

  data() {
    return {
      count: 0,
      courseFlexbox: "course-flexbox",

      courseLists: [
        {
          id: 1,
          courseName: "Intro to Vue 3",
          courseCredit: 50,
          courseHour: 150,
          courseDiscription: "xxxxxxxxxxxxxx",
          studentNum: 20,
        },
        {
          id: 2,
          courseName: "Vue CLI and Vite",
          courseCredit: 20,
          courseHour: 120,
          courseDiscription: "xxxxxxxxxxxxxx",
          studentNum: 19,
        },
        {
          id: 3,
          courseName: "Vue 3 Composition API",
          courseCredit: 20,
          courseHour: 120,
          courseDiscription: "xxxxxxxxxxxxxx",
          studentNum: 19,
        },
        {
          id: 4,
          courseName: "From Vue 2 to Vue 3 ",
          courseCredit: 20,
          courseHour: 120,
          courseDiscription: "xxxxxxxxxxxxxx",
          studentNum: 14,
        },
      ],
    };
  },

  methods: {
    addOne() {
      this.count++;
    },
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.course-flexbox {
  margin-top: 3rem;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
