<template>
  <div id="app">
    <div :class="[$style.header]">
      <h1>My Personal Costs</h1>
    </div>
    <div class="wrapper">
      <ShowPaymentForm @showPaymentForm="visiblePaymentForm" />
      <AddPaymentForm @addNewPayment="addNewPaymentData" v-show="visible" />
      <br />
      <PaymentsDisplay :items="paymentsList" />
    </div>
  </div>
</template>

<script>
import PaymentsDisplay from "./components/PaymentsDisplay.vue";
import AddPaymentForm from "./components/AddPaymentForm.vue";
import ShowPaymentForm from "./components/ShowPaymentForm.vue";
export default {
  name: "App",
  components: {
    PaymentsDisplay,
    AddPaymentForm,
    ShowPaymentForm,
  },
  data() {
    return {
      paymentsList: [],
      visible: false,
    };
  },
  methods: {
    addNewPaymentData(value) {
      this.paymentsList = [...this.paymentsList, value];
    },
    visiblePaymentForm() {
      this.visible = !this.visible;
    },
    fetchData() {
      return [
        {
          date: "12.03.2020",
          category: "Food",
          value: 180,
        },
        {
          date: "12.04.2020",
          category: "Internet",
          value: 100,
        },
        {
          date: "28.08.2019",
          category: "Food",
          value: 300,
        },
        {
          date: "11.03.2018",
          category: "Sport",
          value: 1400,
        },
        {
          date: "17.04.2020",
          category: "Food",
          value: 750,
        },
        {
          date: "02.08.2020",
          category: "Apparel",
          value: 990,
        },
        {
          date: "21.11.2020",
          category: "Health",
          value: 250,
        },
      ];
    },
  },
  created() {
    this.paymentsList = this.fetchData();
  },
};
</script>

<style lang="scss" scoped module>
.header {
  font-size: 20px;
}
</style>