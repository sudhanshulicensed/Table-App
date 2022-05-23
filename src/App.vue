<template>
  <div id="app">
    <div class="component">
      <div class="form-modal"><FormModal :inputData="tableData"/></div>
      <div class="form-to-tab"><FormToTable :savedTable="tableData" /></div>
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
    }
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
