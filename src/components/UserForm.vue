<template>
  <form @submit.prevent="handleSubmit" class="form-wrapper">
    <img
      class="logo-image"
      src="../assets/greentech-logo.png"
      alt="Greentech Logo"
    />

    <h2 class="form-title">Have us reach out</h2>

    <div class="input-group floating-label">
      <input
        v-model="form.first"
        id="first"
        type="text"
        placeholder=" "
        required
      />
      <label for="first">First Name</label>
    </div>

    <div class="input-group floating-label">
      <input
        v-model="form.last"
        id="last"
        type="text"
        placeholder=" "
        required
      />
      <label for="last">Last Name</label>
    </div>

    <div class="input-group floating-label">
      <input
        v-model="form.email"
        id="email"
        type="email"
        placeholder=" "
        required
      />
      <label for="email">Email</label>
    </div>

    <div class="input-group floating-label">
      <input
        v-model="form.phone"
        id="phone"
        type="text"
        placeholder=" "
        @input="formatPhone"
      />
      <label for="phone">Phone Number</label>
    </div>

    <div class="input-group floating-label">
      <input v-model="form.company" id="company" type="text" placeholder=" " />
      <label for="company">Company</label>
    </div>

    <button type="submit" class="submit-button">Continue</button>
  </form>
</template>

<script setup>
import { reactive } from "vue";
import axios from "axios";

const emit = defineEmits(["submitted"]);

// Holding user input
const form = reactive({
  first: "",
  last: "",
  email: "",
  phone: "",
  company: "",
});

// Format phone number to (000) 000-0000
const formatPhone = () => {
  let digits = form.phone.replace(/\D/g, "");
  if (digits.length > 0) {
    digits = digits.slice(0, 10);
    form.phone = `(${digits.slice(0, 3)}) ${digits.slice(3, 6)}-${digits.slice(
      6
    )}`;
  }
};

const handleSubmit = async () => {
  try {
    // Post the form data to the API
    await axios.post(
      "https://dev-api-api.hiring-test.experientialpreview.com/api/lead/7adc2204-1353-40cc-99a3-b37d1a0961ef",
      {
        ...form,
        phone: form.phone.replace(/\D/g, ""),
      }
    );

    emit("submitted");
    // Reset the form
    Object.keys(form).forEach((key) => {
      form[key] = "";
    });
  } catch (error) {
    console.error("Submission failed:", error);
  }
};
</script>

<style scoped>
@import url("https://fonts.googleapis.com/css2?family=ABeeZee&display=swap");

/* Overall wrapper */
.form-wrapper {
  width: 393px;
  height: 852px;
  background: #f4f2ee;
  position: relative;
  font-family: "ABeeZee", sans-serif;
  box-sizing: border-box;
}

/* Geentech logo */
.logo-image {
  position: absolute;
  width: 122.83px;
  height: 40px;
  top: 30px;
  left: 35px;
}

/* Form title */
.form-title {
  position: absolute;
  width: 310px;
  height: 29px;
  top: 208px;
  left: 36px;
  font-family: "Roboto", sans-serif;
  font-weight: 400;
  font-size: 25px;
  line-height: 100%;
  color: #555552;
  margin: 0;
}

/* Input container */
.floating-label {
  position: absolute;
  left: 35.76px;
  width: 310px;
  height: 40.32px;
  position: absolute;
}

/* Top positions of each input box */
.floating-label:nth-of-type(1) {
  top: 262.95px;
}
.floating-label:nth-of-type(2) {
  top: 334.23px;
}
.floating-label:nth-of-type(3) {
  top: 405.51px;
}
.floating-label:nth-of-type(4) {
  top: 476.79px;
}
.floating-label:nth-of-type(5) {
  top: 548.07px;
}

/* Input of text box*/
.floating-label input {
  height: 40.32px;
  width: 100%;
  padding: 0px 0px 0px 20.1px; /* top, right, bottom, left */

  font-size: 15px;
  line-height: 100%;
  color: #555552;

  border: 0.72px solid #555552;
  border-radius: 3.6px;
  background: transparent;
  outline: none;
  font-family: "ABeeZee", sans-serif;
}

/* Labels */
.floating-label label {
  position: absolute;
  top: -7.91px;
  left: 20.1px;
  background: #f4f2ee;
  padding: 0 6.32px;
  font-family: "ABeeZee", sans-serif;
  font-weight: 400;
  font-size: 12px;
  line-height: 14px;
  color: #006315;
  pointer-events: none;
  height: 14px;
}

/* Submit button */
.submit-button {
  position: absolute;
  top: 640px;
  left: 215px;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 5.38px;
  padding: 10.22px 37.5px 8.61px 37.5px;
  background-color: #0b476c;
  color: #ffffff;
  border: none;
  border-radius: 4px;
  font-family: "ABeeZee", sans-serif;
  font-size: 13.45px;
  font-weight: 400;
  cursor: pointer;
}
</style>
