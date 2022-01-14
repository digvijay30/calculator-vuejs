<template>
  <section class="cal-bg">
    <Calculator />
  </section>
</template>

<script>
import Calculator from "./components/Calculator.vue";
export default {
  components: {
    Calculator,
  },
  data() {
    return {
      abc: "a",
    };
  },
};
</script>
<style>
*
{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
  .cal-bg{
    height: 100vh;
    width: 100vw;
    background: #99c089;
    display:flex;
    justify-content: center;
    align-items: center;
  }
</style>