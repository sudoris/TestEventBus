<template>
  <div>
    <component :is="compName"></component
    <br>
    <button @click="increment">Increment</button>
  </div>
</template>

<script>
import { EventBus } from "../main.js"
import ObjectComponent from "./ObjectComponent"

export default {
  name: "NoteEditor",
  components: {
    ObjectComponent
  },
  data() {
    return {
      data: {},
      compName: "ObjectComponent"
    };
  },
  methods: {
    increment() {
      this.data.profile.age++
    }
  },
  watch: {
    data: {
      handler() {
        EventBus.$emit('dataChanged', this.data)
      },
      deep: true
    }
  },
  created() {
    this.data = {
      profile: {
          name: "David",
          age: 34
        }
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>

</style>
