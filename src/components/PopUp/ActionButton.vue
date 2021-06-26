<template>
  <div>
      <div :disabled="isDisabled" class="button-text-container"
        v-bind:class="[isDisabled ? disabledContainer : activeContainer]"
        v-on="{ [!isDisabled ? 'click' : null]: emitClick }"
      >
          <div class="button-text" v-bind:class="[isDisabled ? disabledText : activeText]">
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
        },
        textColor: String
    },
    data() {
        return {
            disabledContainer: 'disabled-container',
            activeContainer: 'active-container',
            disabledText: 'disabled-text',
            activeText: 'active-text',
        }
    },
    methods: {
        emitClick: function () {
            this.$emit('button-clicked')
        }
    }
}
</script>

<style>
.disabled-container {
    opacity: 0.5;
    background-color: #EFFAFF;
}
.active-container {
    cursor: pointer;
}
.disabled-text {
    opacity: 0.5;
}
.active-text {
    cursor: pointer;
}
.button-text-container {
    height: 34px;
    width: 60px;
    background-color:#EFFAFF;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    border-radius:5px;
}
.button-text {
    color: #57ADD3;
    height: 18px;
    width: 33px;
    font-family: Nunito;
    font-size: 15px;
    font-weight: 600;
    letter-spacing: 0;
    line-height: 18px;
    text-align: center;
}

</style>