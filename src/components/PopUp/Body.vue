<template>
  <div class="modal-body">
    
    <div class="image-upload">
      <!-- Image upload and display -->
    </div>
    <div class="name-input">
      <!-- Name input -->
    </div>
  </div>
</template>
<script>
export default {
  name: "Body",
};
</script>

<style lang="scss" scoped>
.modal-body {
  background-color: #f6f8fd;
}
.image-upload {
  margin: 50px auto 28px;
  width: 286px;
  height: 186px;
  background-color: pink;
}
.name-input {
  background-color: grey;
  width: 400px;
  height: 50px;
  margin: 0 auto;
}
</style>