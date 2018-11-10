<template>
  <div>
    <span>{{ this.data }}</span>
  </div>
</template>

<script>
import { EventBus } from "../main.js"

export default {
  name: "ObjectComponent",
  data() {
    return {
      data: null
    }
  },
  created() {
    EventBus.$on("dataChanged", (data) => {
      this.data = data
    })
  }  
}
</script>

<style>

</style>
