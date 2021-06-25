<template>
  <transition name="modal">
    <div class="modal-mask">
        <div class="modal-container">
          <Header v-bind:status="status"/>
          <Body v-bind:status="status"/>
        </div>
    </div>
  </transition>
</template>
<script>
import Header from './Header.vue';
import Body from './Body.vue';

export default {
  name: "PopUp",
  components: {
    Header,
    Body,
  },
  data: function() {
    return {
      status: {
        creatingGroup: true,
        addingMembers: false,
      },
      group: {
        name: "",
        image: "",
        saved: false
      },
      contacts: [],
      members: [] 
    };
  }
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
  background-color: rgba(64,80,105, 0.2);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-container {
  width: 500px;
  min-height: 474px;
  max-height:514px;
  margin: 284px auto 0 auto;
  background-color: #F6F8FD;
  border-radius: 5px;
}
</style>