<template>
  <div>
    <Header 
        v-bind:group="group"
        v-on:close-modal="proceed"
    />
    <Body/>
  </div>
</template>

<script>
import Header from "./Header.vue"
import Body from "./Body.vue"
export default {
  name: "Complete",
  components: {
    Header,
    Body
  },
  props: ['group'],
  methods: {
    proceed() {
      this.$emit("close-modal", "close-modal");
    },
  }
}
</script>

<style>

</style>