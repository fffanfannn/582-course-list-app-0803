<template>
  <div>Course Name</div>
  <p>{{ count }}</p>
  <p>{{ given.name }} - {{ given.id }} -{{ given.age }}</p>
  <button @click="innerAdd">Add</button>
  <button @click="outerAdd">Add to parent</button>
</template>

<script>
export default {
  name: "CourseItem",
  props: {
    given: {
      type: Object,
      required: true,
    },
  },

  data() {
    return {
      count: 0,
    };
  },

  methods: {
    innerAdd() {
      this.count++;
    },
    outerAdd() {
      this.$emit("count-to-parent");
    },
  },
};
</script>
