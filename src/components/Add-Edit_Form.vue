<template>
  <form class="form" action="">
  {{inputData}}
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
        <b-input v-model="email" type="email" value="" maxlength="30"></b-input>
      </b-field>
    </div>
    <div class="input-3">
      <b-field label="Password">
        <b-input v-model="passWord" type="password" value="iwantmytreasure" password-reveal>
        </b-input>
      </b-field>
    </div>
    <div class="date">
      <b-field label="Select a date">
        <b-datepicker
          type="month"
          placeholder="Click to select..."
          icon="calendar-today"
          trap-focus
          v-model="dateOfBirth"
        >
        </b-datepicker>
      </b-field>
    </div>
    <div class="input4">
      <b-checkbox>Accept Terms and Coditions</b-checkbox>
    </div>
    <div class="dialogue">
      <DialogueBox />
    </div>
  </form>
</template>

<script>
import DialogueBox from "./DialogueBox.vue";

export default {
  name: "AddEditForm",
  props: {
    inputData: {
      type: Object,
      default: () => ({}),
    }
  },
  components: {
    DialogueBox,
  },
  data(){
    return{
      check: true,
      firstName: this.inputData.firstName,
      email: this.inputData.firstName,
      passWord: this.inputData.password,
      dateOfBirth: this.inputData.dateOfBirth,
    }
  },
  methods:{
    completeForm(){
      console.log(this.firstName, this.email, this.passWord, this.dateOfBirth);
    },
  }

};
</script>

<style scoped>
.form {
  width: 100%;
  box-sizing: border-box;
  display: flex;
  flex-direction: column;
  row-gap: 10px;
  padding: 20px;
}
</style>
