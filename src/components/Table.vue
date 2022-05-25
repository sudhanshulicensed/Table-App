<template>
  <div class="table">
    <b-table :data="savedTable"
            :paginated="isPaginated"
            :per-page="perPage"
            :current-page.sync="currentPage"
            :pagination-simple="isPaginationSimple"
            :pagination-position="paginationPosition"
            :default-sort-direction="defaultSortDirection"
            :pagination-rounded="isPaginationRounded"
            :sort-icon="sortIcon"
            :sort-icon-size="sortIconSize"
            default-sort="user.first_name"
            aria-next-label="Next page"
            aria-previous-label="Previous page"
            aria-page-label="Page"
            aria-current-label="Current page"
            :page-input="hasInput"
            :pagination-order="paginationOrder"
            :page-input-position="inputPosition"
            :debounce-page-input="inputDebounce">
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
                currentPage: 1,
                perPage: 5,
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
