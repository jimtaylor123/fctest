<template>
  <transition name="modal">
    <div class="modal-mask">
      <div class="modal-container">
        <Header
          v-bind:status="status"
          v-bind:group="group"
          v-on:proceed="proceed"
        />
        <Body v-bind:status="status" />
      </div>
    </div>
  </transition>
</template>
<script>
import Header from "./Header.vue";
import Body from "./Body.vue";

export default {
  name: "PopUp",
  components: {
    Header,
    Body,
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
      console.log(type);
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

        default:
          break;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
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
</style>