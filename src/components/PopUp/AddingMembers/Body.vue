<template>
  <div>
    <ContactSearch/>
    <ContactList/>
  </div>
</template>

<script>
import ContactSearch from "./Contacts/ContactSearch.vue"
import ContactList from "./Contacts/ContactList.vue"
export default {
  name: "AddingMembersBody",
  components: {
    ContactSearch,
    ContactList
  }

}
</script>

<style>

</style>