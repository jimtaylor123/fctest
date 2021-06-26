<template>
  <div class="modal-body">
    
    <div class="image-upload">
      <!-- Icon -->
      <div class="group-icon">
        <GroupIcon/>
      </div>
      <!-- Text -->
      <div class="drag-drop-text">Drag & drop an image, or click to upload</div>
    </div>
    <div class="name-input">
      <input class="search-everything destyle-input" type="text" placeholder="Enter group name" @input="$emit('change-group-name', $event)">
    </div>
  </div>
</template>
<script>
import GroupIcon from "../../Icons/GroupIcon.vue"
export default {
  name: "Body",
  components: {
    GroupIcon,
  }
};
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Nunito&display=swap');
.modal-body {
  background-color: #f6f8fd;
}
.image-upload {
  margin: 50px auto 28px;
  width: 286px;
  height: 186px;
}
.name-input {
  box-sizing: border-box;
  height: 50px;
  width: 400px;
  border: 1px solid #D5DEED;
  border-radius: 25px;
  background-color: #FFFFFF;
  margin:0 auto;
}
.group-icon {
  text-align: center;
  margin-bottom: 20px;
}
.drag-drop-text{
  height: 48px;
  width: 292px;
  color: #96A6BE;
  font-family: 'Nunito', sans-serif;
  font-size: 16px;
  letter-spacing: 0;
  line-height: 24px;
  text-align: center;
}
.search-everything{
  height: 22px;
  width: 121.73px;
  color: #405069;
  font-family: 'Nunito', sans-serif;
  font-size: 14px;
  letter-spacing: 0.1px;
  line-height: 22px;
  border: 0;
  margin-top:12px;
  margin-left:21px;
}
.destyle-input{
  -webkit-appearance: none;
  appearance: none;
  vertical-align: middle;
  color: inherit;
  // font: inherit;
  border: 0;
  background: transparent;
  outline: 0;
  border-radius: 0;
  text-align: inherit;
}
</style>