<template>
  <div class="div-content">
    <h1 id="titulo">Titulo: {{message}}</h1> <!-- interpolacion de texto -->
    <div id="div_v-text">
      <p v-text="description"></p>
    </div>
    <div id="div_v-html">
      <p>You can learn more in <i v-html="textHtml"></i></p>
    </div>
    <div id="div_v-model">
      <input type="text" v-model="inputText" placeholder="write here">
      <p>The message is --> {{inputText}}</p>
      <select v-model="selected">
        <option disabled value="">Seleccione un elemento</option>
        <option>A</option>
        <option>B</option>
        <option>C</option>
      </select>
      <p>You select: {{ selected }}</p>
    </div>
    <div id="div_v-bind">
      <img :src="img" alt=""> <!-- : = v-bind: -->
      <h2 :class="nameClass">This text should be red</h2>
    </div>
    <br>
    <div>
      <button @click="incrementarContador()"> <!-- @ = v-on: -->
        Botón {{contador}}
      </button>
    </div>
    <br>
    <div>
      <input type="text" v-model="inputEvent" @keyup="presionarTecla()">
    </div>
    <br>
    <div>
      <select @change="cambiarColor()" v-model="colorContenedor">
        <option value="contenedor rojo">Rojo</option>
        <option value="contenedor verde">Verde</option>
        <option value="contenedor amarillo">Amarillo</option>
        <option value="contenedor azul">Azul</option>
      </select>
      <div :class="contenedor"></div>
    </div>
    <br>
    <div>
      <form @submit="enviarFormulario()">
        <input type="text" v-model="inputForm">
        <input type="submit" value="Enviar">
      </form>
    </div>
    <br>
    <div>
      <input type="text" @input="cambiarParrafo()" v-model="inputForm">
    </div>
    <br>
    <div>
      <p>{{parrafo}}</p>
    </div>
    <div :class="container">
      <p>{{primerTexto}}{{segundoTexto}}</p>
      <p>{{textoCompleto}}</p>
      <time class="time">{{now.toLocaleDateString()}}</time>
      <br>
      <time class="ti">{{hoy}}</time>
      <br>
      <input type="text" name="" id="" v-model="tercerTexto">
      <button @click="cambiar()">Cambiar</button>
      <br>
      <select name="" id="" v-model="selection">
        <option value="1">1</option>
        <option value="2">2</option>
        <option value="3">3</option>
        <option value="4">4</option>
      </select>
      <br>
      <br>
      <button @click="openDoor = !openDoor">
        {{openDoor? 'cerrar': 'abrir'}}
      </button>
      <br>
      <br>
      <img v-if="openDoor" :src="img" alt=""><!-- v-show   v-if -->
      <img v-else src="https://picsum.photos/200/300?grayscale" alt=""><!-- tambien existe v-else-if -->
      <br>
      <br>
      <p v-for="(persona, index) in listaPersonas" :key="index">
        {{persona}}
      </p>
      <br>
      <br>
      <!-- componentes -->
      <nuevo-componente v-for="(imagen, index) in imagenes" :key="index" 
        :titulo="`imagen ${index+1}`"
        :descripcion="`esta es la imagen ${index+1}`" 
        :imagen="imagen"
        @mostrarAlerta="alertar"
      />
      <!-- componentes con asincronismo -->
      <div class="">
        <!-- <component :is"componente"></component>
        <button @click="cambiarComponente()">Boton</button> -->
        <principal v-if="verComponente"/>
        <br>
        <button @click="verComponente=!verComponente">Ocultar</button>
        <secundario/>
      </div>
    </div>
  </div>
</template>

<script>
import { watch } from '@vue/runtime-core';
/*import Principal from './components/Principal.vue'
import Secundario from './components/Secundario.vue'*/
import { defineAsyncComponent } from 'vue';
const Principal = defineAsyncComponent(() => import("@/components/Principal.vue"))

import NuevoComponente from './components/nuevoComponente.vue';
import Secundario from './components/Secundario.vue';

export default{
  components: { NuevoComponente, Principal, Secundario },
  name:"App", 
  data(){
    //Variabled
    return{
      message: "Hello Vue!",
      description: "Vue is a JavaScript framework for building user interfaces.",
      textHtml: '<a href="https://es.vuejs.org">vueJS</a>',
      inputText: '',
      selected: '',
      img: 'https://picsum.photos/500/300',
      nameClass: "texto-rojo",
      contador: 0,
      inputEvent: '',
      contenedor: 'contenedor',
      colorContenedor: '',
      inputForm: '',
      parrafo: '',
      primerTexto: "Bienvenido",
      segundoTexto: " al curso de VUE",
      tercerTexto: "",
      now: new Date(),
      selection: "",
      container: "cerrado",
      openDoor: false,
      listaPersonas: ['pedro', 'juan', 'ana', 'miguel', 'gabriela','juan'],
      imagenes: [
        'https://picsum.photos/id/217/200/300',
        'https://picsum.photos/id/137/200/300',
        'https://picsum.photos/id/297/200/300',
        'https://picsum.photos/id/187/200/300'
      ],
      
      componente: "Principal",
      verComponente: true,
    }
  },
  //Eventos en Vue
  methods: {
    incrementarContador(){
      this.contador++;
    },

    presionarTecla(){
      alert(this.inputEvent)
    },

    cambiarColor(){
      this.contenedor = this.colorContenedor;
    },

    enviarFormulario(){
      this.parrafo = this.inputForm;
    },

    cambiarParrafo(){
      this.parrafo = this.inputForm;
    },

    cambiar(){
      this.segundoTexto = this.tercerTexto;
    },

    alertar(data){
      alert(data);
    },

    cambiarComponente(){
      if (this.componente == "Principal"){
        this.componente = "Secundario";
      } else{
        this.componente = "Principal";
      }
    }

  },
  //Funciones computadas
  computed: {
    textoCompleto(){
      return this.primerTexto+this.segundoTexto;
    },

    hoy(){
      return this.now.toLocaleDateString();
    },

  },
  //Wachers
  watch: {
    selection(value, old){
      console.log("Se hizo un cambio", value, '-', old);
    },

    openDoor(value){
      value? this.container = 'abierto': this.container = 'cerrado';
    },
  }
}
</script>

<style>

.texto-rojo{
  color: red;
}

.div-content{
  text-align: center;
}

.contenedor{
  width: 100px;
  height: 100px;
  margin: auto;
  background-color: grey;
}

.azul{
  background-color: #070044;
}

.verde{
  background-color: #004400;
}

.rojo{
  background-color: #750101;
}

.amarillo{
  background-color: #b9ae0a;
}

.cerrado {
  background-color: #7e1616;
  padding: 10px;
  border: 5px solid grey;
}

.abierto {
  background-color: #159731;
  padding: 10px;
  border: 5px dotted grey;
}

</style>
