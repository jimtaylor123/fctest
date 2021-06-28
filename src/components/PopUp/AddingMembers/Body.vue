<template>
  <div>
    <ContactSearch/>
    <ContactList v-bind:contacts="contacts" v-on:toggle-member="$emit('toggle-member', $event)"/>
  </div>
</template>

<script>
import ContactSearch from "./Contacts/ContactSearch.vue"
import ContactList from "./Contacts/ContactList.vue"
export default {
  name: "AddingMembersBody",
  props: ['contacts'],
  components: {
    ContactSearch,
    ContactList
  }

}
</script>

<style>

</style>