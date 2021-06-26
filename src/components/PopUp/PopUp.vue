<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-container">
        <div v-if="status.creatingGroup">
          <Creating
            v-bind:group="group"
            v-on:start-adding-members="proceed"
            v-on:change-group-name="changeGroupName"
          />
        </div>
        <div v-else-if="status.addingMembers">
          <AddingMembers
            v-bind:group="group"
            v-on:save-group="proceed"
          />
        </div>
        <div v-else>
          <Complete />
        </div>
      </div>
    </div>
  </transition>
</template>
<script>
import Creating from "./Creating/Creating.vue";
import AddingMembers from "./AddingMembers/AddingMembers.vue";
import Complete from "./Complete/Complete.vue";

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
        image: "",
        members: [],
        saved: false,
      },
      contacts: [],
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
          //TODO save group
          this.status.creatingGroup = false;
          this.status.addingMembers = false;
          break;
        case "close-modal":
          //TODO close modal by emitting close signal
          break;

        default:
          break;
      }
    },
    changeGroupName(name) {
      this.group.name = name;
    }
  },
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