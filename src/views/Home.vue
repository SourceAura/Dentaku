<template>
  <div class="home">
    <Calculator />
  </div>
</template>

<script>
// @ is an alias to /src
import Calculator from "@/components/Calculator.vue";

export default {
  name: "home",
  components: {
    Calculator
  },
  data() {
    return {};
  }
};
</script>

<style lang="css" >

</style>
