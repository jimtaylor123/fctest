<template>
  <div class="image-upload">

    <!-- Hover state -->
    <div v-show="$refs.upload && $refs.upload.dropActive" class="drop-active">
      <h3>Appears when hovering</h3>
    </div>

    <div class="avatar-upload">

      <!-- Image preview -->
      <div class="group-icon">
        <label for="avatar">
          <img :src="files.length ? files[0].url : group.avatar? group.avatar : './group.svg'"  class="rounded-circle" />
        </label>
      </div>

      <!-- File upload input -->
      <div class="text-center p-2">
        <file-upload
          extensions="gif,jpg,jpeg,png,webp"
          accept="image/png,image/gif,image/jpeg,image/webp"
          name="avatar"
          class="drag-drop-text"
          :drop="true"
          v-model="files"
          @input-filter="saveImage"
          ref="upload">
          Drag & drop an image, or click to upload
        </file-upload>
      </div>

    </div>

  </div>
</template>
<style>

.image-upload {
  margin: 50px auto 28px;
  width: 286px;
  height: 186px;
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

.group-icon {
  text-align: center;
  margin-bottom: 20px;
}

.avatar-upload .rounded-circle {
  width: 144px;
  height: 144px;
  border-radius: 50%;
}
/* .example-avatar .text-center .btn {
  margin: 0 .5rem

}
.example-avatar .avatar-edit-image {
  max-width: 100%
} */

/* .example-avatar .drop-active {
  top: 0;
  bottom: 0;
  right: 0;
  left: 0;
  position: fixed;
  z-index: 9999;
  opacity: .6;
  text-align: center;
  background: #000;
}

.example-avatar .drop-active h3 {
  margin: -.5em 0 0;
  position: absolute;
  top: 50%;
  left: 0;
  right: 0;
  -webkit-transform: translateY(-50%);
  -ms-transform: translateY(-50%);
  transform: translateY(-50%);
  font-size: 40px;
  color: #fff;
  padding: 0;
} */

</style>

<script>
import FileUpload from 'vue-upload-component'
export default {
  components: {
    FileUpload,
  },
  props: ['group'],

  data() {
    return {
      files: [],
      image: ''
    }
  },


  methods: {

    saveImage(newFile, oldFile, prevent) {

      if (newFile && !oldFile) {
        if (!/\.(gif|jpg|jpeg|png|webp)$/i.test(newFile.name)) {
          alert('Your choice is not a picture')
          return prevent()
        }
      }

      if (newFile && (!oldFile || newFile.file !== oldFile.file)) {

        const reader = new FileReader();

        reader.onload = (e) => {
            this.image = e.target.result;
            this.$emit('image', this.image);
        };

        reader.readAsDataURL(newFile.file);
        newFile.url = ''
        let URL = window.URL || window.webkitURL
        if (URL && URL.createObjectURL) {
          newFile.url = URL.createObjectURL(newFile.file)
        }
      }
    }
  }
}
</script>