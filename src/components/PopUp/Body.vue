<template>
    <div class="modal-body">
        <slot name="body">default body</slot>
    </div>
</template>
<script>
export default {
  name: "Body",
};
</script>

<style lang="scss" scoped>
.modal-body {
//   margin: 20px 0;
  background-color: #F6F8FD;
}
</style>