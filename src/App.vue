<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
  <h1>Course List App</h1>
  <p>{{ count }}</p>
  <CourseItem v-bind:v-for="courselist in courselists" :given="courselist" />
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
      courselists: [
        { id: 1, name: "AA", age: 15 },
        { id: 2, name: "BB", age: 17 },
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
