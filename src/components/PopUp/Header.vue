<template>
    <div class="modal-header">
        <div v-if="status.creatingGroup">
            <CreatingHeader/>
        </div>
        <div v-else-if="status.addingMembers">
            <AddingMembersHeader/>
        </div>
        <div v-else>
             <CompleteHeader/>
        </div>
    </div>
</template>
<script>
import CreatingHeader from './Headers/Creating.vue';
import AddingMembersHeader from './Headers/AddingMembers.vue';
import CompleteHeader from './Headers/Complete.vue';
export default {
  name: "Header",
  props: ['status'],
  components:{
      CreatingHeader,
      AddingMembersHeader,
      CompleteHeader
  }
};
</script>

<style lang="scss" scoped>

.modal-header {
    height: 54px;
    background-color: #FFFFFF;
    border-radius: 5px;
}

</style>