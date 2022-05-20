<template>
  <div class="table">
    <b-table :data="savedTable" :columns="columns"></b-table>
  </div>
</template>

<script>
export default {
  name: "FormToTable",
  props: {
    savedTable : {
      type: Array,
      default: () => [],
    }
  },
  data() {
    return {
      columns: [
        {
          field: "fiName",
          label: "First Name",
        },
        {
          field: "eMail",
          label: "Email",
        },
        {
          field: "dOb",
          label: "Date of Birth",
          centered: true,
        },
      ],
    };
  },
};
</script>

<style scoped>
    .table{
        width: 60%;
        margin-left: auto;
        margin-right: auto;
    }
</style>
