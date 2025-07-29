<template>
  <div class="thank-you-wrapper">
    <img src="@/assets/greentech-logo.png" alt="GreenTech" class="logo-image" />
    <div class="thank-message">
      <p class="top-text">Thank you</p>
      <p class="bottom-text">We will contact you shortly</p>
    </div>
  </div>
</template>

<script setup></script>

<style scoped>
.thank-you-wrapper {
  width: 393px;
  height: 852px;
  background: #f4f2ee;
  position: relative;
  box-sizing: border-box;
}
.logo-image {
  position: absolute;
  width: 122.83px;
  height: 40px;
  top: 30px;
  left: 35px;
}

.thank-message {
  position: absolute;
  width: 227px;
  height: 116px;
  top: 366px;
  left: 83px;

  font-family: "Roboto", sans-serif;
  font-weight: 400;
  font-size: 25px;
  line-height: 100%;
  letter-spacing: 0;
  color: #555552;

  text-align: center;
  position: absolute;
}
/* position top and bottom of div */
.thank-message .top-text {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
}

.thank-message .bottom-text {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
}
</style>
