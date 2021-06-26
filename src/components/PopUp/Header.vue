<template>
  <div class="modal-header">
    <div v-if="status.creatingGroup">
      <CreatingHeader
        v-bind:group="group"
        v-on:start-adding-members="proceed('start-adding-members')"
      />
    </div>
    <div v-else-if="status.addingMembers">
      <AddingMembersHeader
        v-bind:group="group"
         v-on:save-group="proceed('save-group')"
      />
    </div>
    <div v-else>
      <CompleteHeader />
    </div>
  </div>
</template>
<script>
import CreatingHeader from "./Headers/Creating.vue";
import AddingMembersHeader from "./Headers/AddingMembers.vue";
import CompleteHeader from "./Headers/Complete.vue";
export default {
  name: "Header",
  props: ["status", "group"],
  components: {
    CreatingHeader,
    AddingMembersHeader,
    CompleteHeader,
  },
  methods: {
    proceed(type) {
      this.$emit("proceed", type);
    },
  },
};
</script>

<style lang="scss" scoped>
.modal-header {
  height: 54px;
  background-color: #ffffff;
  border-radius: 5px;
}
</style>