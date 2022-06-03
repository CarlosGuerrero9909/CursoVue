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
  </div>
</template>

<script>
export default{
  name:"App", 
  data(){
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

  },
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
  background-color: #440000;
}

.amarillo{
  background-color: #3a4400;
}

</style>
