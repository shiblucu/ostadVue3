<script setup>
import { ref } from 'vue';

const num1 = ref(null);
const num2 = ref(null);
const operator = ref('+');
const result = ref(null);

const calculate = () => {
    switch (operator.value) {
        case '+':
            result.value = num1.value + num2.value;
            break;
        case '-':
            result.value = num1.value - num2.value;
            break;
        case '*':
            result.value = num1.value * num2.value;
            break;
        case '/':
            if (num2.value !== 0) {
                result.value = num1.value / num2.value;
            } else {
                result.value = 'Cannot divide by zero';
            }
            break;
        default:
            result.value = null;
    }
};
</script>
<template>
    <div>
        <h2>Calculator</h2>
        <div>
            <input v-model.number="num1" type="number" placeholder="Enter number 1">
            <input v-model.number="num2" type="number" placeholder="Enter number 2">
        </div>
        <div>
            <select v-model="operator">
                <option value="+">+</option>
                <option value="-">-</option>
                <option value="*">*</option>
                <option value="/">/</option>
            </select>
        </div>
        <button @click="calculate">Calculate</button>
        <div v-if="result !== null">Result: {{ result }}</div>
    </div>
</template>
  
<style scoped>
/* Add styling here */
</style>
  