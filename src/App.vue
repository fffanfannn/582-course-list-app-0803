<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  <h1>Course List App</h1>
  <p>Course selected: {{ count }}</p>
  <CourseItem
    v-for="courseList in courseLists"
    :key="courseList.id"
    :given="courseList"
    @count-to-parent="addOne"
  />
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

      courseLists: [
        {
          id: 1,
          courseName: "Web Project",
          courseCredit: 50,
          courseHour: 150,
          courseDiscription: "xxxxxxxxxxxxxx",
          studentNum: 20,
        },
        {
          id: 2,
          courseName: "Web Creation & Design",
          courseCredit: 20,
          courseHour: 120,
          courseDiscription: "xxxxxxxxxxxxxx",
          studentNum: 19,
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
</style>
