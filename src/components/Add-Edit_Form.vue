<template>
  <form class="form" action="">
    <div class="form-title">
      <p>Add-Data to Table</p>
    </div>
    <div class="input-1">
      <b-field label="Name">
        <b-input v-model="name"></b-input>
      </b-field>
    </div>
    <div class="input-2">
      <b-field label="Email" type="is-danger" message="This email is invalid">
        <b-input type="email" value="john@" maxlength="30"> </b-input>
      </b-field>
    </div>
    <div class="input-3">
      <b-field label="Password">
        <b-input type="password" value="iwantmytreasure" password-reveal>
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
        >
        </b-datepicker>
      </b-field>
    </div>
    <div class="input4">
      <b-checkbox v-model="hasError">Accept Terms and Coditions</b-checkbox>
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
  components: {
    DialogueBox,
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
}
</style>
