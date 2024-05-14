<template>

  <section class="src-componentes-atributos">
    <div class="jumbotron">
      <h2>Componentes Atributos</h2>
      <hr>

      <!--    --------------------------   -->
      <!--             :style              -->
      <!--    --------------------------   -->
      <h4><u>:style</u></h4>
      <button class="btn btn-success my-3" @click="estado1=!estado1">Cambiar</button>
      <!-- <p style="background-color: red; color:white; border-radius:10px;padding: 10px"> -->
      <p :style="{'background-color': estado1 ? 'pink' : 'blue', 'color':'white', 'border-radius':'10px', 'padding':'10px'}">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Eligendi nisi 
        praesentium distinctio sequi laudantium, culpa possimus quisquam natus aspernatur 
        magni aperiam consequatur illo incidunt reiciendis, doloribus eos perspiciatis 
        excepturi debitis?
      </p>

      <!--    --------------------------   -->
      <!--             :class              -->
      <!--    --------------------------   -->
      <h4><u>:class</u></h4>
      <button class="btn btn-success my-3" @click="estado2=!estado2">Cambiar Color Fondo</button>
      <!-- <p class="btn btn-success"> -->
      <!-- <p :class="{btn: true, 'btn-success': estado2, 'btn-danger': !estado2}"> -->
      <p :class="[btn, 'p-3', {'btn-success': estado2, 'btn-danger': !estado2}]">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Eligendi nisi 
        praesentium distinctio sequi laudantium, culpa possimus quisquam natus aspernatur 
        magni aperiam consequatur illo incidunt reiciendis, doloribus eos perspiciatis 
        excepturi debitis?
      </p>

    </div>
  </section>
</template>

<script lang="js">

  export default  {
    name: 'src-componentes-atributos',
    props: [],
    mounted () {

    },
    data () {
      return {
          estado1: true,
          estado2: true,

      }
    },
    methods: {

    },
    computed: {

    }
}


</script>

<style scoped lang="css">
  .jumbotron{
    background-color: green;
    color: black;
  }
  h2{
    color: black;
  }
  hr{
    background-color: #eee;
  }
</style>
