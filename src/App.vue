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
      nameClass: "texto-rojo"
    }
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

</style>
