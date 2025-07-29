<template>
  <Form v-if="!submitted" @submitted="handleSubmitted" />
  <ThankYou v-else />
</template>

<script setup>
import Form from "./components/UserForm.vue";
import ThankYou from "./components/ThankYou.vue";
import { ref } from "vue";

const submitted = ref(false);

const handleSubmitted = () => {
  submitted.value = true;
  setTimeout(() => {
    submitted.value = false;
  }, 5000);
};
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

form,
.form-wrapper {
  border: none;
  outline: none;
}

input:focus,
button:focus {
  outline: none;
  box-shadow: none;
}
html,
body {
  width: 393px;
  height: 852px;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background: #f4f2ee;
}
</style>
