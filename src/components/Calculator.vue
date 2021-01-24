<template>
  <div class="container text-center">
    <img class="m-auto mb-12" alt="Vue logo" src="../assets/logo.png" />
    <h3>Addition Calculator</h3>
    <form class="my-6" id="sumComp">
      <div class="flex justify-center items-center">
        <input type="text" class="form-control" v-model="numbers.num1" />
        <button class="mr-6" type="button" @click="decrementValue('num1')">
          decrement -
        </button>
        <button type="button" @click="incrementValue('num1')">
          increment +
        </button>
      </div>
      <div class="flex justify-center items-center">
        <input type="text" class="form-control" v-model="numbers.num2" />
        <button class="mr-6" type="button" @click="decrementValue('num2')">
          decrement -
        </button>
        <button type="button" @click="incrementValue('num2')">
          increment +
        </button>
      </div>

      <button class="mt-6" @click="addNumbers" type="button">Add me!</button>
    </form>
    <p><strong>Sum:</strong> {{ parseInt(getValue) }}</p>
  </div>
</template>
<script lang="ts">
interface Numbers {
  num1: number;
  num2: number;
}

import { ref, reactive, defineComponent, computed } from "vue";
export default defineComponent({
  setup() {
    let sum = ref(0);

    const numbers = reactive<Numbers>({ num1: 0, num2: 0 });

    const incrementValue = (modification) => {
      numbers[modification]++;
    };

    const decrementValue = (modification) => {
      numbers[modification]--;
    };

    const addNumbers = () => {
      sum.value = numbers.num1 + numbers.num2;
    };

    const getValue = computed(() => sum.value);

    return {
      sum,
      getValue,
      numbers,
      addNumbers,
      incrementValue,
      decrementValue,
    };
  },
});
</script>
