<template>
  <div class="calculator">
    <div class="display">{{ current || "0" }}</div>
    <vs-button type="line" @click="clear" class="btn" color="white"
      >C</vs-button
    >
    <vs-button type="line" @click="sign" class="btn" color="white"
      >+/-</vs-button
    >
    <vs-button type="line" @click="percent" class="btn" color="white"
      >%</vs-button
    >

    <!-- ops -->
    <vs-button type="line" @click="divide" class="btn operator" color="orange"
      >/</vs-button
    >
    <!--  class="btn" -->
    <vs-button type="line" @click="append('7')" class="btn" color="white"
      >7</vs-button
    >
    <vs-button type="line" @click="append('8')" class="btn" color="white"
      >8</vs-button
    >
    <vs-button type="line" @click="append('9')" class="btn" color="white"
      >9</vs-button
    >
    <!-- ops -->
    <vs-button type="line" @click="multiply" class="btn operator" color="orange"
      >x</vs-button
    >
    <!--  class="btn" -->
    <vs-button type="line" @click="append('4')" class="btn" color="white"
      >4</vs-button
    >
    <vs-button type="line" @click="append('5')" class="btn" color="white"
      >5</vs-button
    >
    <vs-button type="line" @click="append('6')" class="btn" color="white"
      >6</vs-button
    >
    <!-- ops -->
    <vs-button type="line" @click="subtract" class="btn operator" color="orange"
      >-</vs-button
    >
    <!--  class="btn" -->
    <vs-button type="line" @click="append('1')" class="btn" color="white"
      >1</vs-button
    >
    <vs-button type="line" @click="append('2')" class="btn" color="white"
      >2</vs-button
    >
    <vs-button type="line" @click="append('3')" class="btn" color="white"
      >3</vs-button
    >
    <!-- ops -->
    <vs-button type="line" @click="add" class="btn operator" color="orange"
      >+</vs-button
    >
    <!-- sero -->
    <vs-button type="line" @click="append('0')" class="btn zero" color="white"
      >0</vs-button
    >
    <vs-button type="line" @click="dot('.')" class="btn" color="white"
      >.</vs-button
    >
    <!-- ops -->
    <vs-button type="line" @click="compute" class="btn operator" color="orange"
      >=</vs-button
    >
  </div>
</template>

<script>
export default {
  name: "Calculator",
  data() {
    return {
      current: "",
      previous: null,
      operator: null,
      executed: false
    };
  },
  props: {},
  methods: {
    clear() {
      // resets calculator display current
      this.current = "";
    },
    sign() {
      // appends minus symbol if it doesn't exist
      // if it does it is removed.
      this.current =
        this.current.charAt(0) === "-"
          ? this.current.slice(1)
          : `-${this.current}`;
    },
    percent() {
      // divides current current - makes it a float...and yada ya
      this.current = `${parseFloat(this.current) / 100}`;
    },

    //
    append(number) {
      if (this.executed) {
        this.current = "";
        this.executed = false;
      }
      // this.current + number || concatonate.
      this.current = `${this.current}${number}`;
    },
    dot() {
      // only append the dot/decimal IF it isn't present.
      if (this.current.indexOf(".") === -1) {
        this.append(".");
      }
    },
    // operators - ^_^
    setPrevious() {
      this.executed = true;
      this.previous = this.current;
    },
    // the fun part huh
    divide() {
      this.operator = (a, b) => a / b;
      this.setPrevious();
    },
    multiply() {
      this.operator = (a, b) => a * b;
      this.setPrevious();
    },
    subtract() {
      this.operator = (a, b) => a - b;
      this.setPrevious();
    },
    add() {
      this.operator = (a, b) => a + b;
      this.setPrevious();

      // if (this.current.indexOf('+') === -1) {
      //   this.append('+');
      // }
    },
    compute() {
      this.current = this.operator(
        parseFloat(this.current),
        parseFloat(this.previous)
      );
      this.previous = null;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="css" scoped>
@import url("https://fonts.googleapis.com/css?family=Shadows+Into+Light&display=swap");

.calculator {
  border: 7px;
}
.display {
  font-size: 31px;
  box-shadow: 13px;
  padding-top: 7px;
  border-radius: 7px;
  font-family: "Shadows Into Light", cursive;
}

.btn {
  padding-top: 13px;
  font-size: 21px;
  border-radius: 73px;
  /* border: 0.7px solid; */
  color: whitesmoke;

  background-color: rgb(255, 159, 15 0.9);
  font-family: "Shadows Into Light", cursive;
}
.zero {
  grid-column: 1 / 3;
}
.display {
  /* starts at col 1 ends at 4 */
  grid-column: 1 / 5;
  text-align: center;
  color: whitesmoke;
  background-color: rgb(0, 0, 0 0.1);
}
.operator {
  color: white;
  text-align: center;
  /* background-color: rgb(255, 153, 0); */
}
.calculator {
  width: 310px;
  display: grid;
  margin: 0 auto;
  margin-top: 50px;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
}
</style>
