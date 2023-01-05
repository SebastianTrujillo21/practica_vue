<script setup>
import { ref } from 'vue'
let nombre = "Pedro";
const colorStyle = "color:blue";
const arrayColor = ["red", "blue", "peru"];
const arrayFrutas = ["🍉", "🍊", "🍋", "🍎", "🍒"];
const validacion = true;
const arrayLargo = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    stock: 0,
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    stock: 10,
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
    stock: 20,
  },
];

const array_mas_largo = [
  {
    name: "Manzana",
    price: "$1.00",
    description: "Una manzana",
    stock: 0,
  },
  {
    name: "Pera",
    price: "$2.00",
    description: "Una pera",
    stock: 10,
  },
  {
    name: "Naranja",
    price: "$3.00",
    description: "Una naranja",
    stock: 20,
  }];

//metodo - methods
const handleClick = (text) => {
  console.log("Me diste click " + text);
}

let counter = ref(0)

const increment = () => {
  counter.value++;
}

const decrement = () => {
  counter.value--;
}

const returnToZero = () => {
  counter.value = 0
}

</script>

<template>
  <h1>HOLA a todos menos a {{ nombre.toUpperCase() }}</h1>
  <h2 v-bind:style="colorStyle">Soy azul</h2>
  <h2>{{ arrayColor }}</h2>
  <h2 :style="`color:${arrayColor[2]}`">Que pedo wey</h2>
  <h2>{{ validacion== true ? "Soy verdadero" : "Soy falso" }}</h2>
  <h2 v-if="validacion">Hola macacos</h2>
  <!-- <h2 v-if="!validacion">ADIOS MACACOS</h2> -->
  <h2 v-else>Adios macacos</h2>
  <h2 v-show="validacion">Estoy activo v-show</h2>
  <br>
  <ul>
    <li v-for="(fruta, index) in arrayFrutas" :key="index">
      {{ index }} - {{ fruta }}
    </li>
  </ul>

  <ul>
    <li v-for="(fruta, index) in arrayLargo" :key="fruta.name">
      {{ fruta.name }}-{{ fruta.price }} - {{ fruta.stock }}
    </li>
  </ul>

  <br>
  <ul>
    <template v-for="(fruta, index) in array_mas_largo" :key="fruta.name">
      <li v-if="fruta.stock > 0">
        {{ fruta.name }} - {{ fruta.price }} - {{ fruta.stock }}
      </li>
    </template>
  </ul>

  <br>
  <button v-on:click.middle="handleClick('MIDDLE')">Activame MIDDLE</button>
  <button v-on:click.right.prevent="handleClick('RIGHT')">Activame Right</button>
  <button @click="handleClick('LEFT')">Activame Left</button>

  <br>
 <!-- MI SOLUCION
   <template v-if="counter > 0">
    <h2 style="color:green">{{ counter }}</h2>
  </template>
  <template v-if="counter < 0">
    <h2 style="color:red">{{ counter }}</h2>
  </template>-->
  <h2 v-bind:class="counter>0? 'positive':'negative'">{{ counter }}</h2>
  <button @click="increment">Aumentar</button>
  <button @click="decrement">Decrecer</button>
  <button @click="returnToZero">Volver a 0</button>

</template>

<style>
h1 {
  color: red;
}

.positive {
  color: green;
}

.negative {
  color: red;
}
</style>