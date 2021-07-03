<template>
  <div>
    <input
      type="number"
      v-model.number="operand1"
      placeholder="0"
      id="operand1"
      value=""
      :disabled="radioSelected === 'two'"
    />
    <input
      type="number"
      v-model.number="operand2"
      placeholder="0"
      id="operand2"
      value=""
      :disabled="radioSelected === 'one'"
    />
    <p>= {{ result }}</p>
    <div class="keyboard">
      <button @click="sum">+</button>
      <button @click="sub">-</button>
      <button @click="multiply">*</button>
      <button @click="divide">/</button>
      <button @click="pow">^</button>
      <button @click="divide2">~</button>
    </div>
    <br />
    <div class="checkbox">
      <input type="checkbox" id="checkbox" v-model="selected" />
      <label for="checkbox">Отобразить клавиатуру</label>
      <div v-show="selected">
        <br />
        <button
          class="digits"
          v-for="digit in digits"
          @click="typing"
          :key="digit"
          :value="digit"
        >
          {{ digit }}
        </button>
      </div>
    </div>
    <br />
    <div>
      <input
        type="radio"
        class="radio"
        name="one"
        id="one"
        value="operand1"
        v-model="picked"
        @click="pad"
      />
      <label for="one">operand1</label>

      <input
        type="radio"
        class="radio"
        name="two"
        id="two"
        value="operand2"
        @click="pad"
        v-model="picked"
      />
      <label for="two">operand2</label>
      <br />
      <span></span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      operand1: "",
      operand2: "",
      result: 0,
      digits: [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, "<"],
      picked: "operand1",
      radioSelected: "one",
      selected: false,
    };
  },

  methods: {
    sum() {
      this.result = +this.operand1 + +this.operand2;
    },
    sub() {
      this.result = this.operand1 - this.operand2;
    },
    multiply() {
      this.result = this.operand1 * this.operand2;
    },
    divide() {
      if (+this.operand2 === 0) {
        this.result = "Ошибка! На ноль делить нельзя!";
      } else {
        this.result = this.operand1 / this.operand2;
      }
    },
    pow() {
      this.result = Math.pow(this.operand1, this.operand2);
    },
    divide2() {
      if (+this.operand2 === 0) {
        this.result = "Ошибка! На ноль делить нельзя!";
      } else {
        this.result = Math.round(this.operand1 / this.operand2);
      }
    },

    pad(event) {
      this.radioSelected = event.target.id;
    },

    typing(event) {
      let key = event.target.value;
      if (this.radioSelected === "one") {
        if (key === "<") {
          this.operand1 = this.operand1.substr(0, this.operand1.length - 1);
        } else {
          this.operand1 += key;
        }
      }

      if (this.radioSelected === "two") {
        if (key === "<") {
          this.operand2 = this.operand2.substr(0, this.operand2.length - 1);
        } else {
          this.operand2 += key;
        }
      }
    },
  },
};
</script>
<style scoped>
button {
  padding: 5px 10px;
  background-color: lightblue;
  color: blue;
}
</style>

