<template>
    <div class="main_component">
        <div class="card">
            <h1 class="titulo">{{titulo}}</h1>
        <img class="img" :src="imagen" alt="">
        <p class="desc">{{descripcion}}</p>
        <button @click="responderPadre(titulo)">Boton</button>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        titulo: "",
        descripcion: "",
        imagen: "",
    },
    methods:{
        responderPadre(data){
            this.$emit("mostrarAlerta", `Hola soy ${data}`)
        }
    }

};
</script>

<style>
.main_component{
    display: flex;
    /*align-content: center;
    justify-content: space-between;*/
    flex-direction: row;
}
.card{
    border: 2px #b1a8a8 solid;
    width: 40%;
    padding: 10px;
    margin: 10px;
}
.titulo{

}
.img{

}
.desc{

}
</style>