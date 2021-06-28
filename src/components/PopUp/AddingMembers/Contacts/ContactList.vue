<template>
  <div class="contact-list">
    <div v-for="contact in contacts" v-bind:key="contact.id">
      <Contact v-bind:contact="contact" v-on:toggle-member="toggleMember"/>
    </div>
  </div>
</template>

<script>
import Contact from './Contact.vue'
export default {
  components:{
    Contact
  },
  name: "ContactList",
  props: ["contacts"],
  methods:{
    toggleMember(contactId){
      this.$emit('toggle-member', contactId)
    }
  }
};
</script>

<style scoped>
.contact-list{
  overflow-y:scroll;
  height: 370px;
  width: 500px;
  background-color: #F6F8FD;
}
</style>