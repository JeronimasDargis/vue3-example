<template>
  <div class="container text-center">
    <img class="m-auto mb-12" alt="Vue logo" src="../assets/logo.png" />
    <h3>Addition Calculator</h3>
    <form id="sumComp">
      <div class="flex justify-center items-center">
        <input type="text" class="form-control" v-model="numbers.num1" />
        <button type="button" @click="incrementValue('num1')">
          increment +
        </button>
      </div>
      <div class="flex justify-center items-center">
        <input type="text" class="form-control" v-model="numbers.num2" />
        <button type="button" @click="incrementValue('num2')">
          increment +
        </button>
      </div>

      <button @click="addNumbers" type="button">Add me!</button>
    </form>
    <p><strong>Sum:</strong> {{ sum }}</p>
  </div>
</template>
<script>
import { ref, reactive } from "vue";
export default {
  setup() {
    let sum = ref(0);

    const numbers = reactive({ num1: 0, num2: 0 });

    const incrementValue = (modification) => {
      numbers[modification]++;
    };

    const addNumbers = () => {
      sum.value = parseInt(numbers.num1) + parseInt(numbers.num2);
    };
    return {
      sum,
      numbers,
      addNumbers,
      incrementValue,
    };
  },
};
</script>
