<template>

  <section class="src-componentes-binding">
    <div class="jumbotron">
      <h2>Componente Binding</h2>
      <hr>
        <!-- ------------------------------- -->
        <!-- Interpolacion / v-text / v-html -->
        <!-- ------------------------------- -->
        <h4><u>Interpolacion / v-text / v-html</u></h4>
        <br>
        <p>{{ mensaje }}</p>
        <p v-text="mensaje"></p> <!-- directivas del framework. v-text es un atributo -->
        <p v-html="mensaje"></p>
        <br>
        <p>{{ mensajeHTML }}</p> <!-- Muestra tal cual el msj-->
        <p v-text="mensajeHTML"></p> <!-- Muestra tal cual el msj-->
        <p v-html="mensajeHTML"></p> <!-- Muestra el texto con la aplicacion de la etiqueta html-->
        <hr>
        <!-- ------------------------------- -->
        <!--    Property Binding / v-bind    -->
        <!-- ------------------------------- -->
        <h4><u>Property Binding / v-bind</u></h4>
        <br>
        <input type="text" value="123"> <br>
        <input type="text" value="valor"> <br>
        <br>
        <input type="text" v-bind:value="valor"> {{valor}}<br>
        <input type="text" :value="valor"> {{valor}}<br> <!-- Es lo mismo que la linea 36-->
        <input type="text" value="valor"> {{valor}}<br>
        <!--------- BINDEO DE PROPIEDADES --------->
        <hr>
        <!-- ------------------------------ -->
        <!--      Event Binding / v-on      -->
        <!-- ------------------------------ -->
        <h4><u> Event Binding / v-on</u></h4>
        <br>
        <!-- https://www.w3schools.com/js/js_events.asp -->
        <button class="btn btn-success my-3 mr-2" v-on:click="contador++">Contar {{contador}}</button>            
        <button class="btn btn-success my-3 mr-2" v-on:click="contador2++">Contar {{contador2}}</button>            
        <button class="btn btn-success my-3" @click="incrementar()">Contar {{getContador3()}}</button> <!-- el @ es lo mismo que poner v-on:-->            
        <hr>
        <!--------- BINDEO BIDIRECCIONAL --------->
        <!--   ------------------------------   -->
        <!--     Doble Data Binding / v-model   -->
        <!--   ------------------------------   -->
        <h4><u> Doble Data Binding / v-model</u></h4>
        <h5>Manual</h5>
        <!-- <input type="text" v-bind:value="valor2" v-on:input="actualizar($event)"> {{valor2}}<br>  -->
        <input type="text" :value="valor2" @input="actualizar($event)"> {{valor2}}<br> 
        <br>
        <h5>Automatico</h5>
        <input type="text" v-model="valor3"> {{valor3}}<br> <!-- muy utilizado en formularios-->
    </div>
  </section>

</template>

<script lang="js">

  export default  {
    name: 'src-componentes-binding',
    props: [],
    mounted () {

    },
    data () {
      return {
          mensaje: 'Soy un mensaje',
          mensajeHTML: '<i>Soy un mensaje</i>',
          valor: 456,
          valor2: 789,
          valor3: 321,
          contador: 0,
          contador2: 123,
          contador3: 456,
      }
    },
    methods: {
        incrementar(){
            this.contador3++;
        },
        getContador3(){
            return this.contador3;
        },
        actualizar(e){
            //console.log("actualizar",e);
            const dato = e.target.value;
            //console.log(dato);
            this.valor2 = dato;
        },
    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .jumbotron{
    background-color: blue;
    color: white;
  }
  h2{
    color: white;
  }
  hr{
    background-color: #eee;
  }
</style>
