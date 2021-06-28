<template>
  <div class="search-container">
      <div class="search-input">
          <div class="search-input-left">
            <img :src="'./search.svg'" class="search-icon">
            <input type="text" class="search-everything destyle-input" placeholder="Search">
          </div>
          <CloseIcon v-bind:margins="['19px', '20px', '19px', '0']" size="12px"/>
      </div>
  </div>
</template>

<script>
import CloseIcon from "../../../Icons/CloseIcon.vue"
export default {
    name: "ContactSearch",
    components: {
        CloseIcon
    }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito&display=swap');
.search-container{
    height: 70px;
    background-color: #F6F8FD;
    box-shadow: 0 0 50px 0 rgba(223,231,242,0.5);
}
.search-input{
    height: 50px;
    background-color:#FFFFFF;
    border-radius: 25px;
    margin:20px;
    display: flex;
    justify-content: space-between;
}
.search-input-left {
    display: flex;
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
.search-icon{
    margin: 14px 12px 16px 14px;
}
.search-everything{
    height: 22px;
    width: 138.67px;
    color: #405069;
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    letter-spacing: 0.1px;
    line-height: 22px;
    margin-top:12px;
}
</style>