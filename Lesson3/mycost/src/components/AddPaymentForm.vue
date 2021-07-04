<template>
  <div class="payment-form">
    <input
      class="payment-form-input"
      placeholder="Payment date"
      type="text"
      v-model.trim="date"
    />
    <br />
    <input
      class="payment-form-input"
      placeholder="Payment category"
      type="text"
      v-model.trim="category"
    />
    <br />
    <input
      class="payment-form-input"
      placeholder="Payment amount"
      type="number"
      v-model.number="value"
    />
    <br />
    <button class="payment-form-button" @click="addButtonClick">ADD +</button>
  </div>
</template>

<script>
export default {
  name: "AddPaymentForm",
  data() {
    return {
      value: "",
      category: "",
      date: "",
    };
  },
  methods: {
    getCurrentDate() {
      const today = new Date();
      const d = today.getDate();
      const m = today.getMonth() + 1;
      const y = today.getFullYear();
      return `${d}.${m}.${y}`;
    },
    addButtonClick() {
      const { value, category } = this;
      const data = {
        date: this.date || this.getCurrentDate(),
        category,
        value,
      };
      this.$emit("addNewPayment", data);
    },
  },
};
</script>

<style>
.payment-form-button {
  background-color: teal;
  color: white;
  padding: 10px;
  border: teal;
  width: 150px;
  margin-top: 10px;
  margin-bottom: 10px;
}
.payment-form-input {
  margin: 5px 0 5px;
  padding: 5px;
}
</style>

