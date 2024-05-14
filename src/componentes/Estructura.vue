<template>

  <section class="src-componentes-estructura">
    <div class="jumbotron">
      <h2>Componentes Estructura</h2>
      <hr>

      <!--  ------  -->
      <!--   v-if   -->
      <!--  ------  -->

      <h4><u>v-if</u></h4>
      <button class="btn btn-info my-3" @click="mostrar = !mostrar">
        {{ mostrar ? "Ocultar" : "Mostrar" }}
      </button>
      <p v-if="mostrar" class="alert alert-warning">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Magni deserunt 
        fugiat veritatis officiis deleniti? Veniam laborum dignissimos quibusdam officia 
        consequuntur enim aperiam delectus expedita aspernatur saepe! Temporibus omnis 
        asperiores eligendi!
      </p>

      <p v-else class="alert alert-danger">
        ELEMENTO REMOVIDO
      </p>

      <!--  --------  -->
      <!--   v-show   -->
      <!--  --------  -->
      <h4><u>v-show</u></h4>

      <button class="btn btn-info my-3" @click="cambiarVisibilidad()">
        {{ obtenerTituloVisibilidad() }}
      </button>
      <p v-show="visibilidad()" class="alert alert-warning">
        Lorem ipsum dolor sit amet, consectetur adipisicing elit. Magni deserunt 
        fugiat veritatis officiis deleniti? Veniam laborum dignissimos quibusdam officia 
        consequuntur enim aperiam delectus expedita aspernatur saepe! Temporibus omnis 
        asperiores eligendi!
      </p>

      <!--  -------  -->
      <!--   v-for   -->
      <!--  -------  -->
      <h4><u>v-for</u></h4>
      <br>
      <ul>
        <!-- <li>{{ usuarios[0] }}</li>
        <li>{{ usuarios[1] }}</li>
        <li>{{ usuarios[2] }}</li>
        <li>{{ usuarios[3] }}</li> -->
        <li v-for="(usuario,index) in usuarios" :key="index">
        {{ index+1 }} - {{ usuario }}
        </li>
      </ul>
      <hr>
      <button class="btn btn-warning my-3" @click="agregarAlumno()">Agregar Alumno</button>
      <div v-if="alumnos.length">

        <ul>
          <li v-for="(alumno,index) in alumnos" :key="index">
          <!-- <pre>{{ index+1 }} - {{ alumno }}</pre> -->
          <!-- {{ alumno.nombre }} {{ alumno.apellido }} -->
          <!-- {{ index+1 }} - {{ alumno.nombre }} {{ alumno.apellido }} -->
          <!-- {{ (index + 1) +' - ' + alumno.nombre + ' '+ alumno.apellido }} -->
          {{ `${index + 1} - ${alumno.nombre} ${alumno.apellido}` }}
          </li>
        </ul>
        <hr>
        <div class="table-responsive">
          <table class="table table-dark">
            <tr>
              <th>Nombre</th>
              <th>Apellido</th>
              <th>Edad</th>
              <th>Curso</th>
              <th>Foto</th>
            </tr>
            <tr v-for="(alumno,index) in alumnos" :key="index">
              <td>{{ alumno.nombre }}</td>
              <td>{{ alumno.apellido }}</td>
              <td>{{ alumno.edad }}</td>
              <td>{{ alumno.curso ? 'Si' : 'No'}}</td>
              <td>
                <img :src="alumno.foto" :alt="alumno.nombre" width="50">
              </td>
            </tr>
          </table>

          <!--  ---------------------------  -->
          <!--   v-if / v-else-if / v-else   -->
          <!--  ---------------------------  -->

          <h4 class="alert alert-primary">
            <span v-if="obtenerDatosAlumnos.cantidad == 0">Ningun alumno hizo el curso</span>
            <span v-else-if="obtenerDatosAlumnos.cantidad == obtenerDatosAlumnos.total">Todos los alumnos hicieron el curso</span>
            <span v-else>{{ obtenerDatosAlumnos.cantidad }} de {{ obtenerDatosAlumnos.total }} alumnos hicieron el curso</span>
        </h4>
        </div>
        <br>

        <div v-for="(alumno,index) in alumnos" :key="index" class="media alert alert-danger">
          <img :src="alumno.foto" width="150" class="mr-3" :alt="alumno.nombre">
          <div class="media-body">
            <h5 class="mt-0"><u>Orden: {{ index +1 }}</u></h5>
            <br>
              <p>Nombre: <a :href="alumno.foto">{{ alumno.nombre }} {{ alumno.apellido }}</a></p>
              <p>Edad: <i>{{alumno.edad}}</i></p>
              Hizo el curso: <input type="checkbox" v-model="alumno.curso"> <!--Utilizo el double databinding-->
            <buttom class="btn btn-danger mx-3" @click="borrarAlumno(index)">Borrar</buttom>
          </div>
        </div>
     </div>
     <h4 v-else class="alert alert-danger">No se encontraron alumnos</h4>
    </div>
  </section>
</template>

<script lang="js">

  export default  {
    name: 'src-componentes-estructura',
    props: [],
    mounted () {

    },
    data () {
      return {
        mostrar: true,
        mostrar2: true,
        usuarios: [
          'Pedro',
          'Juan',
          'Ana',
          'Laura',
        ],
        //https://www.iconfinder.com/iconsets/business-avatar-1
        alumnos: [
          { nombre: 'Pedro', apellido: 'Mei', edad: 32, curso: true, foto: 'https://cdn3.iconfinder.com/data/icons/business-avatar-1/512/1_avatar-512.png'},
          { nombre: 'Juan', apellido: 'Blanco', edad: 24, curso: false, foto: 'https://cdn3.iconfinder.com/data/icons/business-avatar-1/512/2_avatar-512.png'},
          { nombre: 'Ana', apellido: 'Perez', edad: 31, curso: false, foto: 'https://cdn3.iconfinder.com/data/icons/business-avatar-1/512/11_avatar-512.png'},
          { nombre: 'Laura', apellido: 'Lopez', edad: 26, curso: true, foto: 'https://cdn3.iconfinder.com/data/icons/business-avatar-1/512/4_avatar-512.png'},
        ],
      }
    },
    methods: {
      cambiarVisibilidad() {
        this.mostrar2 = !this.mostrar2
      },
      obtenerTituloVisibilidad(){
        return this.mostrar2 ? "Ocultar":"Mostrar" 
      },
      visibilidad(){
        return this.mostrar2;
      },
      borrarAlumno(index){
        console.log('borrarAlumno',index)
        this.alumnos.splice(index,1)
      },
      agregarAlumno(){
          const alumno = {nombre: 'Pablo', apellido: 'Gutierrez', edad: 28, curso: false, foto: 'https://cdn3.iconfinder.com/data/icons/business-avatar-1/512/8_avatar-512.png'}
          this.alumnos.push(alumno);
        },
    },
    computed: {
      obtenerDatosAlumnos(){
        let cant = 0;
        this.alumnos.forEach(alumnos => {
          if(alumnos.curso) cant++
        });
        return {
          cantidad: cant,
          total: this.alumnos.length,
        }
      },
    }
}


</script>

<style scoped lang="css">
  .jumbotron{
    background-color: pink;
    color: brown;
  }
  h2{
    color: brown;
  }
  hr{
    background-color: #000;
  }
  .table td, .table th{
    vertical-align: middle;
  }
</style>
