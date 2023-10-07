<script setup>
import { ref } from 'vue'

const UserInput = ref('')
// Operation functions
const append = (value) => {
  UserInput.value += value
}
// clear  function
const clear = () => {
    UserInput.value = ''
}

// Check which operation to display the result 
const checkOperation = () => {
  const input = UserInput.value;
  let result = 0;

  // Check for addition
  if (input.includes('+')) {
    const operands = input.split('+');
    result = operands.reduce((acc, operand) => acc + parseFloat(operand), 0);
  }

  // Check for subtraction
  else if (input.includes('-')) {
    const operands = input.split('-');
    result = operands.reduce((acc, operand) => acc - parseFloat(operand), 0);
  }

  // Check for multiplication
  else if (input.includes('x')) {
    const operands = input.split('x');
    result = operands.reduce((acc, operand) => acc * parseFloat(operand), 1);
  }

  // Check for division
  else if (input.includes('/')) {
    const operands = input.split('/');
    result = operands.reduce((acc, operand) => acc / parseFloat(operand), 1);
  }

  // Check for modulus
  else if (input.includes('%')) {
    const operands = input.split('%');
    result = operands[0] % operands[1];
  }

    UserInput.value = result.toString();
  
}

</script>

<template>
<div class="container">

    <div>
        <input type="text" name="" id="" v-model='UserInput'  class="text-area">
    </div>
    <div class="buts">
        <!-- Digit buttons -->
    <button  @click="append('1')">1</button>
    <button  @click="append('2')">2</button>
    <button  @click="append('3')">3</button>
    <button  @click="append('4')">4</button>
    <button  @click="append('5')">5</button>
    <button  @click="append('6')">6</button>
    <button  @click="append('7')">7</button>
    <button  @click="append('8')">8</button>
    <button  @click="append('9')">9</button>
    <button  @click="append('0')">0</button>
    <button  @click="append('.')">.</button>
    <button  @click="clear">C</button>

    <!-- operator buttons -->

    <button  @click="append('%')" class="button-operator">%</button>
    <button  @click="append('/')" class="button-operator">/</button>
    <button  @click="append('x')" class="button-operator">x</button>
    <button  @click="append('-')" class="button-operator">-</button>
    <button  @click="append('+')" class="button-operator">+</button>
    <button  @click="checkOperation" class="equals">=</button>

    </div>
    

</div>
</template>

<style scoped>
/* Calculator container */
.container {
  width: 300px;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
  background-color: #f5f5f5;
  box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.2);
}

/* Calculator display */
.text-area {
  margin-bottom: 10px;
  padding: 10px;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 5px;
  font-size: 24px;
  text-align: right;
  width: 250px;

}

/* Calculator buttons */
.buts {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-gap: 10px;
}

button {
  padding: 10px;
  font-size: 18px;
  border: 1px solid #ccc;
  border-radius: 5px;
  cursor: pointer;
  background-color: #fff;
}

/* Style specific buttons differently */
.button-operator {
  background-color: #ff9800;
  color: #fff;
}

/* Style the equals button */
button.equals {
  background-color: #009688;
  color: #fff;
}
</style>
