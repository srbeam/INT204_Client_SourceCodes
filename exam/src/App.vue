<script setup>
import { ref } from 'vue'
const profile = [63130500116,"Sarisa Phulakorn"]


const randNumbers = ref([])
// generates random number in range (1-99)
const generateNumber = () => {
  let duplicate = false
  const rand = Math.floor(Math.random() * 99 + 1)
  duplicate = randNumbers.value.some((randNumber) => randNumber === rand)
  duplicate ? generateNumber() : randNumbers.value.push(rand)
}

const isDisabled = ref(false)
const buttonSwitch = ()=>{
  isDisabled.value = isDisabled.value;
  console.log(isDisabled.value)
}
</script>

<template>
<div>
  <p style="color:blueviolet"> {{ profile }}</p>
</div>
  <div class="top-container">
    <div class="action-button">
      <button v-on:click="randNumbers">Generate New Number</button>
      <button>Reset</button>
    </div>
    <div class="error-message">
      <!-- show error message when a user adding the same number in the bingo sheet -->
      <p> Sorry, Your number is already exist in the bingo
        sheet,please generate new number again!
      </p>
    </div>
    <div class="grid-container">
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      <div class="grid-item">
        <button :disabled="!isDisabled">Add Number</button>
      </div>
      

    </div>
    <div class="generate-number">
      <!-- show the list of generated number here -->
      <ul>
        <p v-for="(randNumber,index) in randNumbers" :key="index" >Generate Number #{{index}} : '{{randNumber}}'</p>
      </ul>
    </div>
  </div>
  <div>

  </div>
</template>

<style scoped>
.top-container {
  width: 330px;
}
.action-button {
  padding: 10px;
  display: flex;
  gap: 5px;
}
.grid-container {
  display: grid;
  grid-template-columns: 100px 100px 100px;
  grid-template-rows: 80px 80px 80px;
  column-gap: 5px;
  row-gap: 5px;
  background-color: green;
  padding: 10px;
}
.grid-item {
  display: flex;
  background-color: rgba(255, 255, 255, 0.8);
  border: 1px solid rgba(0, 0, 0, 0.8);
  font-size: 30px;
  text-align: center;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
.generate-number {
  font-size: 20px;
}
.error-message {
  height: 40px;
  color: red;
}
</style>
