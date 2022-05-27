<template>
  <div class="div">
    <h1>Saludo: {{mensaje}}</h1>
    <h2 :class="clasePruebas" v-text="texto"></h2>
    <h3>--> {{inputText}}</h3>
    <p v-html="textoHtml"></p>
    <input type="text" v-model="inputText"><br>
    <img :src="img" alt=""> <!-- : = v-bind: -->
  </div>
</template>

<script>
export default{
  name:"App", 
  data(){
    return{
      mensaje: "Hola Vue!",
      texto: "Vue Framework",
      textoHtml: '<a href="https://es.vuejs.org">Vue (es)</a>',
      inputText: 'Escribe un texto',
      img: 'https://picsum.photos/500/300',
      clasePruebas: "texto-rojo"
    }
  }
}
</script>

<style>
.texto-azul{
  color: blue;
}

.texto-rojo{
  color: red;
}

</style>
