<template>
  <div>
    <Header v-bind:group="group" v-on:start-adding-members="proceed" v-on:close-modal="$emit('close-modal', 'close-modal')"/>
    <CreatingBody v-bind:group="group" v-on:change-group-name="changeGroupName" v-on:image="$emit('image', $event)"/>
  </div>
</template>

<script>
import Header from "./Header.vue"
import CreatingBody from "./Body.vue"
export default {
  name: "Creating",
  components: {
    Header,
    CreatingBody
  },
  props: ['group'],
  methods: {
    proceed() {
      this.$emit("start-adding-members", "start-adding-members");
    },
    changeGroupName(event){
      this.$emit('change-group-name', event.target.value);
    }
  }
}
</script>

<style lang="scss" scoped>

</style>