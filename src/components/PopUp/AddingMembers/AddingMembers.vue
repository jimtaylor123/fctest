<template>
  <div>
    <Header 
        v-bind:group="group"
        v-on:save-group="proceed"
    />
    <Body/>
  </div>
</template>

<script>
import Header from "./Header.vue"
import Body from "./Body.vue"
export default {
  name: "AddingMembers",
  components: {
    Header,
    Body
  },
  props: ['group'],
  methods: {
    proceed() {
      this.$emit("start-adding-members", "save-group");
    },
  }
}
</script>

<style>

</style>