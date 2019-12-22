<template>
  <div class="calculator">
   
      <div class="display">{{ current || "0" }}</div>

      <span @click="clear" class="btn">C</span>
      <span @click="sign" class="btn">+/-</span>
      <span @click="percent" class="btn">%</span>
      <!-- ops -->
      <span @click="divide" class="btn operator">/</span>
      <!--  class="btn" -->
      <span @click="append('7')" class="btn">7</span>
      <span @click="append('8')" class="btn">8</span>
      <span @click="append('9')" class="btn">9</span>
      <!-- ops -->
      <span @click="multiply" class="btn operator">X</span>
      <!--  class="btn" -->
      <span @click="append('4')" class="btn">4</span>
      <span @click="append('5')" class="btn">5</span>
      <span @click="append('6')" class="btn">6</span>
      <!-- ops -->
      <span @click="subtract" class="btn operator">-</span>
      <!--  class="btn" -->
      <span @click="append('1')" class="btn">1</span>
      <span @click="append('2')" class="btn">2</span>
      <span @click="append('3')" class="btn">3</span>
      <!-- ops -->
      <span @click="add" class="btn operator">+</span>
      <!--  -->
      <span @click="append('0')" class="btn zero">0</span>
      <span @click="dot('.')" class="btn">.</span>
      <!-- ops -->
      <span @click="compute" class="btn operator">=</span>
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
<style scoped>
.calculator {
  border: 7px;
}
.display {
  font-size: 31px;
  box-shadow: 13px;
  padding-top: 7px;
  border-radius: 7px;
}

.btn {
  padding-top: 13px;
  font-size: 21px;
  border-radius: 7px;
  /* border: 0.7px solid; */
  color: whitesmoke;
  background-color: rgb(255, 159, 15 0.9);
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
  background-color: rgb(255, 153, 0);
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
