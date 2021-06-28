<template>
  <div class="modal-header">
    <div class="flex-between">
      <div @click="$emit('close-modal')">
      <CloseIcon />
      </div>

      <div class="flex-between heading-group">
        <div class="title">New Group</div>
        <ActionButton
          text="Next"
          v-bind:isDisabled="nextDisabled"
          v-on:button-clicked="moveOn"
        />
      </div>
    </div>
  </div>
</template>

<script>
import CloseIcon from "../../Icons/CloseIcon.vue";
import ActionButton from "../ActionButton.vue";
export default {
  name: "CreatingHeader",
  props: ["group"],
  components: {
    CloseIcon,
    ActionButton,
  },
  computed: {
    nextDisabled: function () {
      return this.group.name.trim() === "" || this.group.avatar.trim() === "";
    },
  },
  methods: {
    moveOn: function () {
      this.$emit("start-adding-members", "start-adding-members");
    },
  },
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Nunito&display=swap");
.flex-between {
  display: flex;
  justify-content: space-between;
}
.title {
  height: 56px;
  width: 94px;
  color: #405069;
  font-family: "Nunito", sans-serif;
  font-size: 18px;
  letter-spacing: 0;
  line-height: 28px;
  text-align: center;
  margin-top: 5px;
}
.heading-group {
  height: 61px;
  width: 287px;
  margin-top: 10px;
  margin-right: 10px;
}
</style>