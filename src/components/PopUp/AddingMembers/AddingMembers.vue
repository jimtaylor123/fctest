<template>
  <div>
    <Header 
        v-bind:group="group"
        v-on:save-group="proceed"
        v-on:go-back="$emit('go-back')"
    />
    <Body v-bind:contacts="contacts" v-on:toggle-member="$emit('toggle-member', $event)"/>
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
  props: ['group', 'contacts'],
  methods: {
    proceed() {
      this.$emit("save-group", "save-group");
    }
  }
}
</script>

<style>

</style>