<template>
  <div class="add-members-header">
    <!-- back arrow -->
    <BackIcon/>
    <!-- group members -->
    <div class="group-members-title">
      Group Members
    </div>
    <!-- save button -->
    <div class="action-button-wrapper">
    <ActionButton 
          text="Save" 
          v-bind:isDisabled="saveDisabled" 
          v-on:button-clicked="moveOn"
        />
    </div>

  </div>
</template>

<script>
import BackIcon from '../../Icons/BackIcon.vue'
import ActionButton from '../ActionButton.vue'
export default {
    name: "AddingMembersHeader",
    props: ["group"],
    components: {
      BackIcon,
      ActionButton
    },
    computed: {
    saveDisabled: function () {
      return this.group.members.length < 1;
    },
  },
  methods: {
    moveOn: function () {
       this.$emit('save-group', 'save')
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito&display=swap');
.add-members-header{
  display: flex;
  justify-content: space-between;
}
.group-members-title {
  height: 28px;
  width: 134px;
  color: #405069;
  font-family: 'Nunito', sans-serif;
  font-size: 18px;
  letter-spacing: 0;
  line-height: 28px;
  text-align: center;
  margin-top:15px;
  margin-bottom: 11px;
}
.action-button-wrapper{
  margin-top:10px;
  margin-right: 9px;
}

</style>