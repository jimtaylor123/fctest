<template>
  <div class="contact">
      <div class="contact-left">
          <img :src="contact.avatar" :alt="`${contact.first_name} ${contact.last_name}`" class="avatar">
          <div class="contact-name">
              {{`${contact.first_name} ${contact.last_name}`}}
          </div>
      </div>
      <div class="icon-container" @click="toggleMembership">
          <div v-if="!isMember">
            <AddIcon/>
          </div>
          <div v-else>
              <CheckIcon/>
          </div>
      </div>
  </div>
</template>

<script>
import AddIcon from '../../../Icons/AddIcon.vue'
import CheckIcon from '../../../Icons/CheckIcon.vue'
export default {
    name: "Contact",
    components: {
        AddIcon,
        CheckIcon
    },
    props: ['contact'],
    data() {
        return {
            isMember: false
        }
    },
    methods:{
        toggleMembership(){
            this.isMember = !this.isMember;
            this.$emit('toggle-member', this.contact.id);
        }
    }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@600&display=swap');
.contact{
    height: 60px;
    display:flex;
    justify-content: space-between;
}
.avatar{
    width: 48px;
    height: 48px;
    border-radius:25px;
    margin-top: 6px;
    margin-left:20px;
}
.contact-left{
    display:flex;
}
.contact-name{
    height: 22px;
    color: #405069;
    font-family: 'Nunito', sans-serif;
    font-size: 14px;
    font-weight: 600;
    letter-spacing: 0;
    line-height: 22px;
    margin-left:15px;
    margin-top:17px;
}
.icon-container{
    margin: 13px 20px 13px 0;
    height: 34px;
    width: 125px;
    display:flex;
    justify-content: flex-end;
}

</style>