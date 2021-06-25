<template>
  <div>
      <!-- Close icon -->
      <div class="flex-between">
        <CloseIcon/>

      <!-- Title and next container -->
        <!-- Title -->
        <!-- Next -->
        <div class="flex-between heading-group">
            <div class="title">
                New Group
            </div>
            <ActionButton text="Next"/>
        </div>
      </div>

     
  </div>
</template>

<script>
import CloseIcon from './../../Icons/CloseIcon.vue'
import ActionButton from '../ActionButton.vue'

export default {
    name: "CreatingHeader",
    components: {
        CloseIcon,
        ActionButton
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Nunito&display=swap');
.flex-between {
    display:flex;
    justify-content: space-between;
}
.title {
  height: 56px;
  width: 94px;
  color: #405069;
  font-family: 'Nunito', sans-serif;
  font-size: 18px;
  letter-spacing: 0;
  line-height: 28px;
  text-align: center;
  margin-top:5px;
}
.heading-group {
    height: 61px;
    width: 287px;
    margin-top:10px;
    margin-right: 10px;
}
</style>