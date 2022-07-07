.<template>
  <div class="">
    <h2>Hola soy el componente Principal</h2>
    <h3 ref="count">{{contador}}</h3>
    <button @click="contador++">Contar</button>
  </div>
</template>

<script>

export default {
    data() {
        return {
            texto: "Hola vue!!",
            contador: 0,
        }
    },
    methods: {
        alertar(){
            alert("Holaaaaaa")
        }
    },
    beforeCreate() {
        console.log("BeforeCreate ", this.$data, this.$el)
    },
    created() {
        console.log("Created ", this.$data, this.$el)
    },
    mounted() {
        this.alertar();
        console.log("Mounted ", this.$data, this.$el)
    },
    beforeUpdate(){
        console.log("beforeUpdate ", this.$refs['count'].textContent)
        
    },
    updated(){
        console.log("updated ", this.$refs['count'].textContent)
    },
    beforeUnmount(){
        console.log("El elemento va ser desmonatado");
        alert("El elemento se va a ocultar")
    },
    unmounted(){
        console.log("El elemento fue desmontado");
    }

}
</script>

<style>

</style>