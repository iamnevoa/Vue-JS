<template>
  <div>
    <button class="payment-form-button" @click="clickPaymentButton">
      ADD NEW COST +
    </button>
  </div>
</template>

<script>
export default {
  name: "ShowPaymentForm",
  methods: {
    clickPaymentButton() {
      this.$emit("showPaymentForm");
    },
  },
};
</script>

<style>
</style>