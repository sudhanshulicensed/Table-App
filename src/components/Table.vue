<template>
  <div class="table">
    <b-table></b-table>
  </div>
</template>

<script>
export default {
  name: "FormToTable",
  data() {
    return {
      data: [
        {
          id: 1,
          first_name: "",
          email: "Simmons",
          date: "2016-10-15 13:43:27",
          gender: "Male",
        },
      ],
      columns: [
        {
          field: "id",
          label: "ID",
          width: "40",
          numeric: true,
        },
        {
          field: "first_name",
          label: "First Name",
        },
        {
          field: "email",
          label: "Email",
        },
        {
          field: "date",
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
