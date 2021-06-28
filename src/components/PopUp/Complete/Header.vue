<template>
  <div class="modal-header">
    <div class="flex-between">
      <div @click="$emit('close-modal')">
      <CloseIcon />
      </div>

      <div class="flex-between heading-group">
        <div class="title">Group Created</div>
        <div @click="close">
          <ActionButton 
            text="Done" 
            v-bind:isDisabled="false" 
          />
         </div>
      </div>
    </div>
  </div>
</template>

<script>
import CloseIcon from "../../Icons/CloseIcon.vue";
import ActionButton from "../ActionButton.vue";

export default {
  name: "CompleteHeader",
  components: {
    CloseIcon,
    ActionButton,
  },
  props: ["group"],
  computed: {
    nextDisabled: function () {
      return (this.group.name.trim() === "") || (this.group.image.trim() === "");
    },
  },
  methods: {
    close: function () {
      this.$emit('close-modal');
    }
  }
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Nunito&display=swap");
.flex-between {
  display: flex;
  justify-content: space-between;
}
.title {
  height: 28px;
  width: 120px;
  color: #405069;
  font-family: Nunito;
  font-size: 18px;
  letter-spacing: 0;
  line-height: 28px;
  text-align: center;
  margin-top:5px;
}
.heading-group {
  height: 34px;
  width: 298px;
  margin: 10px 12px 10px 0;
}
</style>