<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-container">
        <div v-if="status.creatingGroup">
          <Creating
            v-bind:group="group"
            v-on:start-adding-members="proceed"
            v-on:change-group-name="changeGroupName"
            v-on:image="setImage"
            v-on:close-modal="proceed"
          />
        </div>
        <div v-else-if="status.addingMembers">
          <AddingMembers
            v-bind:group="group"
            v-bind:contacts="contacts"
            v-on:save-group="proceed"
            v-on:toggle-member="toggleMember"
            v-on:go-back="goBack"
          />
        </div>
        <div v-else>
          <Complete  v-on:close-modal="proceed"/>
        </div>
      </div>
    </div>
  </transition>
</template>
<script>
import Creating from "./Creating/Creating.vue";
import AddingMembers from "./AddingMembers/AddingMembers.vue";
import Complete from "./Complete/Complete.vue";
import axios from "axios";

export default {
  name: "PopUp",
  components: {
    Creating,
    AddingMembers,
    Complete
  },
  data: function () {
    return {
      status: {
        creatingGroup: true,
        addingMembers: false,
      },
      group: {
        name: "",
        avatar: "",
        members: []
      },
      contacts: []
    };
  },
  methods: {
    proceed(type) {
      switch (type) {
        case "start-adding-members":
          this.status.creatingGroup = false;
          this.status.addingMembers = true;
          break;
        case "save-group":
          this.saveGroup();
          break;
        case "close-modal":
          //TODO close modal by emitting close signal
          alert('this would close the modal');
          break;

        default:
          break;
      }
    },
    changeGroupName(name) {
      this.group.name = name;
    },
    setImage(image){
      this.group.avatar = image;
    },
    getContacts(){
      axios.get(`${process.env.VUE_APP_API_URL}/getContacts`,  {
      headers: {
        Authorization: `Bearer ${process.env.VUE_APP_AUTH_TOKEN}`
      }
      })
      .then(response => {
        this.contacts = response.data.contacts;
      });
    },
    toggleMember(contactId){
      if(this.group.members.includes(contactId)){
        this.group.members = this.group.members.filter(memberId => memberId !== contactId);
      } else {
        this.group.members.push(contactId)
      }
    },
    saveGroup(){
      axios.post(`${process.env.VUE_APP_API_URL}/createGroup`, this.group, {
        headers: {
          Authorization: `Bearer ${process.env.VUE_APP_AUTH_TOKEN}`
        }
      })
      .then(() => {
        this.status.creatingGroup = false;
        this.status.addingMembers = false;
      });
    },
    goBack(){
      this.group.members = [];
      this.status.creatingGroup = true;
      this.status.addingMembers = false;
    }
  },
  beforeMount(){
    this.getContacts();
  }
};
</script>

<style>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(64, 80, 105, 0.2);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-container {
  width: 500px;
  min-height: 474px;
  max-height: 514px;
  margin: 284px auto 0 auto;
  background-color: #f6f8fd;
  border-radius: 5px;
}

.modal-header {
  height: 54px;
  background-color: #ffffff;
  border-radius: 5px;
}
</style>