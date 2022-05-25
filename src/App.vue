<template>
  <div id="app">
    <div class="component">
      <div class="form-modal"><FormModal :editInput="val"  :openModal="openModal" :selectedIndex="handleIndex" :inputData="tableData"/></div>
      <div class="form-to-tab"><FormToTable @editDetail="editDetails" @handleSelectedIndex="handleIndex" :savedTable="tableData" /></div>
    </div>
  </div>
</template>

<script>

import FormToTable from "./components/Table.vue"
import FormModal from "./components/Modal.vue"

export default {
  name: 'App',
  components: {
    FormToTable,
    FormModal,
  },
  data(){
    return {
      tableData: [],
      val: null,
      openModal: false,
      selectedIndex: null,
    }
  },
  methods: {
    editDetails(val, openModal) {
      this.val = val;
      this.openModal = openModal;
    },
    checkIndex(num){
      if(num === this.selectedIndex){
        return num
      }
    },
    handleIndex(val){
      this.selectedIndex = (val);
      for(let i = 0; i< this.tableData.length; i++) {
        if(this.tableData[i].iD === this.selectedIndex) {
            this.tableData.splice(i, 1);
        }
       }
    },
  },
}
</script>

<style>
  .component{
    box-sizing: border-box;
    padding: 20px;
    display: flex;
    flex-direction: column;
    row-gap: 50px;
  }
</style>
