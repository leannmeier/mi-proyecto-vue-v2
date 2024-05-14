<template>
  <div class="contain">
    <div class="jumbotron">
      <h1>Bienvenidos a Vue CLI</h1> 
      <h2>Componente principal (App)</h2>
      <br>

      <Binding />
      <Estructura />
      <Atributos />

      <Contador ini="123" fondo='success'/>
      <Contador ini="456" fondo='warning'/>
      <Contador ini="789" fondo='danger'/>

      <Formulario />

    </div>
  </div> 
</template> <!-- seccion de vista-->

<script>
import Binding from './componentes/Binding.vue'
import Estructura from './componentes/Estructura.vue'
import Atributos from './componentes/Atributos.vue'
import Contador from './componentes/Contador/IndexContador.vue'
import Formulario from './componentes/Formulario/IndexFormulario.vue'

export default {
  name: 'App',
  components: {
    Binding,
    Estructura,
    Atributos, 
    Contador,
    Formulario,
  }
}
</script> <!-- seccion de controlador-->

<style>
h1{
  color: crimson;
}
h2{
  color: blue;
}
hr{
  color:black;
}
</style> <!-- seccion de estilos-->
