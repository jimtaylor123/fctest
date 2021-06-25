<template>
  <div id="app">
    <div class="flex">
      <CoreMenu/>
      <SideBar/>
      <Chat/>
    </div>
    <PopUp v-if="showPopUp"/>
  </div>
</template>

<script>
import CoreMenu from './components/CoreMenu.vue';
import SideBar from './components/SideBar.vue';
import Chat from './components/Chat.vue';
import PopUp from './components/PopUp/PopUp.vue';

export default {
  name: 'App',
  components: {
    CoreMenu,
    SideBar,
    Chat,
    PopUp,
  },
  data: function () {
    return {
      showPopUp: true,
    };
  },
}
</script>

<style lang="scss">
html {
  height: 1024px;
  width: 1440px;
}
body {
  margin: 0;
  background-color:#F6F8FD;
}
.flex {
  display: flex;
}
</style>
