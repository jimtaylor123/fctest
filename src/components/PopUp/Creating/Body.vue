<template>
  <div class="modal-body">
    <FileUpload v-on:image="$emit('image', $event)"/>
    <div class="name-input">
      <input class="search-everything destyle-input" type="text" placeholder="Enter group name" @input="$emit('change-group-name', $event)">
    </div>
  </div>
</template>
<script>
import FileUpload from ".././FileUpload.vue"
export default {
  name: "Body",
  components: {
    FileUpload
  }
};
</script>

<style lang="scss" scoped>
@import url('https://fonts.googleapis.com/css2?family=Nunito&display=swap');
.modal-body {
  background-color: #f6f8fd;
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
  border: 0;
  background: transparent;
  outline: 0;
  border-radius: 0;
  text-align: inherit;
}
</style>