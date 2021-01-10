<template>
  <div class="container text-center">
    <img class="m-auto mb-12" alt="Vue logo" src="../assets/logo.png" />
    <h3>Addition Calculator</h3>
    <form id="sumComp">
      <div class="flex justify-center items-center">
        <input type="text" class="form-control" v-model="num1" />
        <button type="button" @click="incrementValue(num1)">increment +</button>
      </div>
      <div class="flex justify-center items-center">
        <input type="text" class="form-control" v-model="num2" />
        <button type="button" @click="incrementValue(num2)">increment +</button>
      </div>

      <button @click="addNumbers" type="button">Add me!</button>
    </form>
    <p><strong>Sum:</strong> {{ sum }}</p>
  </div>
</template>
<script>
import { ref } from "vue";
export default {
  setup() {
    let num1 = ref(1);
    let num2 = ref(2);
    let sum = ref(0);

    const incrementValue = (number) => {
      // i am able to pass dynamic var and display its value in console log
      console.log(ref(number).value);
      // i am unable to change its value
      ref(number).value++;
    };

    const addNumbers = () => {
      sum.value = parseInt(num1.value) + parseInt(num2.value);
    };
    return {
      num1,
      num2,
      sum,
      addNumbers,
      incrementValue,
    };
  },
};
</script>
