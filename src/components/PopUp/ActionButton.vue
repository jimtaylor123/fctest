<template>
  <div>
      <div :disabled="isDisabled" class="button-text-container">
          <div class="button-text">
          {{text}}
          </div>
        </div>
  </div>
</template>

<script>
export default {
    name: "ActionButton",
    props: {
        text: String,
        isDisabled: {
            type: Boolean,
            default: false
        }
    }
}
</script>

<style>
.button-text-container {
    height: 34px;
    width: 60px;
    opacity: 0.5;
    background-color: #EFFAFF;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    border-radius:5px;
}
.button-text {
    height: 18px;
    width: 33px;
    color: #57ADD3;
    font-family: Nunito;
    font-size: 15px;
    font-weight: 600;
    letter-spacing: 0;
    line-height: 18px;
    text-align: center;
}

</style>