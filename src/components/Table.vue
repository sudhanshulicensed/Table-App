<template>
  <div class="table">
    <b-table :data="savedTable">
      <b-table-column field="fiName" label="First Name" centered>
            <template v-slot="props">
              {{ props.row.fiName }}
            </template>
      </b-table-column>
      <b-table-column field="eMail" label="Email"  centered>
            <template v-slot="props">
              {{ props.row.eMail }}
            </template>
      </b-table-column>
      <b-table-column field="dOb" label="Date of Birth" sortable centered>
            <template v-slot="props">
              {{ props.row.dOb }}
              {{ props.row }}
            </template>
      </b-table-column>
      <b-table-column field="action" label="Action" centered>
            <template v-slot="props">
                <div class="btn">
                  <span @click="editDetail(props.row)" class="tag is-success">Edit</span>
                  <span @click="deleteDetail(props.row.iD)" class="tag is-danger">Delete</span>
                </div>
            </template>
      </b-table-column>
    </b-table>
    
  </div>
</template>

<script>
export default {
  name: "FormToTable",
  props: {
    savedTable : {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    editDetail(details){
      this.$emit("editDetail", details, true);
    },
    deleteDetail(val){
      console.log("Table: ", val)
      console.log("Table: ", this.savedTable)
      this.$emit("handleSelectedIndex", val)
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
        {
          field: "iD",
          label: "ID",
        },
        {
          field: "action",
          label: "Action"
        }
      ],
      isPaginated: true,
      isPaginationSimple: false,
      isPaginationRounded: false,
      paginationPosition: 'bottom',
      defaultSortDirection: 'asc',
      sortIcon: 'arrow-up',
      sortIconSize: 'is-small',
      hasInput: false,
      paginationOrder: '',
      inputPosition: '',
      inputDebounce: ''
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
    .btn{
      display: flex;
      column-gap: 5px;
    }
</style>
