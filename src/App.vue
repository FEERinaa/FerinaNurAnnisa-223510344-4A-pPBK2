<template>
  <div id="background" :style="{ backgroundImage: backgroundImage }">
    <div class="container">
      <div id="app" :class="{ stylish: isStylish }">
        <h1 :style="{ fontSize: fontSize + 'px', fontFamily: 'Poppins, sans-serif' }">{{ displayText }}</h1>
        <div class="input-container">
          <input type="text" v-model="inputText" @input="handleInput" class="input-field">
        </div>
        <p :style="{ opacity: isStylish ? 1 : 0.5, fontFamily: 'Poppins, sans-serif' }">
          Kuy bermain Magic dengan tulis nama kamu minimal 5 Huruf ya!!
        </p>
      </div>
    </div>
  </div>
  <footer class="footer">
    <p>FERINA NUR ANNISA - 223510344</p>
  </footer>
</template>

<script setup>
import { ref, watch } from 'vue';


const inputText = ref('');
const isStylish = ref(false);
const fontSize = ref(16);
const backgroundImage = ref('none');
const displayText = ref('');


watch(inputText, (newValue) => {
  if (newValue.length >= 5) {  
    isStylish.value = true;
    fontSize.value = 100;
    backgroundImage.value = "url('/src/assets/bg.jpeg')"; 
    displayText.value = newValue; 
  } else {
    isStylish.value = false;
    fontSize.value = 16;
    backgroundImage.value = 'none'; 
    displayText.value = ''; 
  }
});

const handleInput = () => {
  displayText.value = inputText.value; 
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;400;500&display=swap');

body {
 background-image: url(/src/assets/bg.jpeg); 
  background: cover;
background-size: cover;
background-repeat: no-repeat;
}
#background {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-size: cover;
  background-position: center;
}

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}

#app {
  width: 100%;
  max-width: 640px;
  padding: 30px;
  border-radius: 12px;
  box-shadow: 0 6px 20px rgba(123, 97, 255, 0.2);
  text-align: center;
  font-family: 'Poppins', sans-serif;
}

.input-container {
  position: relative;
}

.input-field {
  width: calc(100% - 40px);
  padding: 15px 20px;
  margin-top: 20px;
  font-size: 18px;
  box-shadow: 0 3px 6px rgba(123, 97, 255, 0.15);
  border: none;
  border-radius: 8px;
  transition: box-shadow 0.3s ease-in-out;
}

.input-field:focus {
  box-shadow: 0 3px 12px rgba(123, 97, 255, 0.35);
}

.stylish h1, .stylish p {
  color: #5a189a;  
}

.stylish input[type="text"] {
  box-shadow: 0 3px 12px rgba(233, 30, 99, 0.4);
}

p {
  margin-top: 20px;
  font-size: 16px;
  transition: opacity 0.3s ease;
}

.footer {
  background-color:transparent;
  padding: 1px;
  text-align: center;
  position: fixed;
  bottom: 0;
  left: 0;
  width: 100%;
}

.hello {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  right: calc(100% + 10px);
  font-size: 24px;
}
</style>
