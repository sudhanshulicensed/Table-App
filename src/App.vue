<template>
  <div id="app">
    <div class="component">
      <AddEditForm />
      <FormToTable />
    </div>
  </div>
</template>

<script>

import AddEditForm from "./components/Add-Edit_Form.vue"
import FormToTable from "./components/Table.vue"

export default {
  name: 'App',
  components: {
    AddEditForm,
    FormToTable,
  }
}
</script>

<style>
  .component{
    
  }
</style>
