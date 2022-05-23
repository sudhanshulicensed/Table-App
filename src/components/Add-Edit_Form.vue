<template>
  <form class="form" action="">
    <!-- {{ inputData }} -->
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
    <div class="dialogue">
      <DialogueBox @sendDetail="addDataToForm" />
    </div>
  </form>
</template>

<script>
import DialogueBox from "./DialogueBox.vue";

export default {
  name: "AddEditForm",
  props: {
    inputData: {
      type: Array,
      default: () => [],
    },
  },
  components: {
    DialogueBox,
  },
  data() {
    return {
      check: true,
      firstName: null,
      email: null,
      password: null,
      dateOfBirth: null,
      inputArray: this.inputData,
    };
  },
  methods: {
    addDataToForm(condition) {
      if (condition == true) {
        if (this.firstName && this.email && this.password && this.dateOfBirth) {
          this.inputArray.push({
            iD: this.id++,
            fiName: this.firstName,
            eMail: this.email,
            dOb: this.dateOfBirth,
          });
        }
        console.log(this.inputData),
        this.firstName= null,
        this.email= null,
        this.password= null,
        this.dateOfBirth= null;
      } else{
        console.log("Data isn't pushed");
      }
    },
  },
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
  background: white;
}

/* .overlay{
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.6);
  backdrop-filter: blur(3px);
  z-index: 5;
} */
</style>
