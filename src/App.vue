<template>
  <div id="app">
    <div class="component">
      <div class="form-modal"><FormModal :inputData="data"/></div>
      <div class="form-to-tab"><FormToTable /></div>
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
      data: {
        tableData: [],
        firstName: "",
        email: "",
        password: "",
        dateOfBirth: "",
      }
    }
  },
  methods: {
    addDataToTable(){
      if(this.firstName && this.email && this.dateOfBirth) {
        console.log(this.firstName, this.email, this.dateOfBirth)
        this.tableData.push({fname: this.firstName, eMail: this.email, dOb: this.dateOfBirth})
      }
    }
  }
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
