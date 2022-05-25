<template>
  <form class="form">
    <div class="form-title">
      <p>Add-Data to Table</p>
    </div>
    <div class="input-1">
      <b-field label="Name">
        <b-input v-model="firstName"></b-input>
      </b-field>
    </div>
    <div class="input-2">
      <b-field label="Email">
        <b-input v-model="email" type="email" maxlength="30"></b-input>
      </b-field>
    </div>
    <div class="input-3">
      <b-field label="Password">
        <b-input
          v-model="password"
          type="password"
          value="iwantmytreasure"
          password-reveal
        >
        </b-input>
      </b-field>
    </div>
    <div class="date">
      <b-field label="Select a date">
        <b-datepicker
          v-model="dateOfBirth"
          type="month"
          placeholder="Click to select..."
          icon="calendar-today"
          trap-focus
        >
        </b-datepicker>
      </b-field>
    </div>
    <div class="input4">
      <b-checkbox>Accept Terms and Conditions</b-checkbox>
    </div>
    <div class="footer">
      <b-button
                v-if="!isEdit"
                label="Add"
                type="is-info"
                size="is-medium"
                @click="addDataToForm"/>
      <b-button
          v-else
          label="Edit"
          type="is-info"
          size="is-medium"
                @click="editDataToForm"/>
    </div>
  </form>
</template>

<script>

export default {
  name: "AddEditForm",
  props: {
    inputData: {
      type: Array,
      default: () => [],
    },
    editInput: {
      type: Object,
      default: () => ({}),
    },
    isEdit: {
      type: Boolean,
      default: false,
    },
    selectedIndex:{
      type: Function,
      default: null,
    }
  },
  data() {
    return {
      check: true,
      firstName: null,
      email: null,
      password: null,
      dateOfBirth: null,
      inputArray: this.inputData,
      id: 0,
    };
  },
  mounted(){
    console.log(this.editInput)
  },
  methods: {
    addDataToForm() {
        if (this.firstName && this.email && this.password && this.dateOfBirth) {
          this.inputArray.push({
            fiName: this.firstName,
            eMail: this.email,
            dOb: this.dateOfBirth,
            iD: ++this.id,
          });
        }
        this.$emit("close", false)
        this.firstName= null,
        this.email= null,
        this.password= null,
        this.dateOfBirth= null;
    },
    editDataToForm(){
      console.log(this.inputArray.findIndex(el => el.iD === this.editInput.iD
    ));
    const objId = this.inputArray.findIndex(el => el.iD === this.editInput.iD);
    this.inputArray[objId].fiName = this.firstName;
    this.inputArray[objId].dOb = this.dateOfBirth;
    this.inputArray[objId].eMail = this.email;
    this.$emit("close", false)
    },
  },
  watch: {
    editInput(newVal, oldValue){
      console.log(newVal, oldValue);
      this.firstName = newVal.fiName;
      this.email = newVal.eMail;
      this.dateOfBirth = newVal.dOb;
    }
  }
};
</script>

<style scoped>
.form {
  background: white;
  margin-left: auto;
  margin-right: auto;
  width: 60%;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  row-gap: 10px;
  padding: 20px;
  border-radius: 5px;
}
</style>
