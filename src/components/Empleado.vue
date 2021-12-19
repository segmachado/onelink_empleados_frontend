<template>
  <table class="table">
    <thead>
    <tr>
      <th scope="col">Documento</th>
      <th scope="col">Nombre</th>
      <th scope="col">Area</th>
      <th scope="col">Sub-area</th>
      <th width="25px"></th>
    </tr>
    </thead>
    <tbody>
    <tr>
      <td v-for="empleado in empleados" :key="empleado.id">{{empleado.numDocumento}}</td>
      <td v-for="empleado in empleados" :key="empleado.id">{{empleado.nombres+' '+empleado.apellidos}}</td>
      <td v-for="empleado in empleados" :key="empleado.id">{{areas.find(y=>y.id===subareas.find(x=>x.id===empleado.subarea).area).nombreArea}}</td>
      <td v-for="empleado in empleados" :key="empleado.id">{{subareas.find(x=>x.id===empleado.subarea).nombreSubArea}}</td>
      <td v-for="empleado in empleados" :key="empleado.id">
        <button v-on:click="edit(empleado.id)" class="btn btn-warning">Editar</button>

      </td>
    </tr>
    </tbody>
  </table>
</template>

<script>
import axios from 'axios'

export default {
  mounted(){
     this.obtenerSubAreas();
     this.obtenerAreas();
     this.obtenerEmpleados();
   },
  data(){
     return {empleados:[],areas:[],subareas:[]}
  },
  methods:{
    edit:function (idempleado){
     alert(idempleado)
    },
    async obtenerEmpleados() {
      try {
        let self=this;
        const api='http://localhost:8000/empleado/'
        const empleados=await axios.get(api).then((response)=>{
          return response.data
        })
        self.empleados=empleados;
      }catch(error){
        return {error}
      }
    },
      async obtenerSubAreas()
      {
        try {
          let self = this;
          const api = 'http://localhost:8000/subarea/'
          const subareas = await axios.get(api).then((response) => {
            return response.data
          })
          self.subareas = subareas;
        } catch (error) {
          return {error}
        }
        },
        async obtenerAreas()
        {
          try {
            let self = this;
            const api = 'http://localhost:8000/area/'
            const areas = await axios.get(api).then((response) => {
              return response.data
            })
            self.areas = areas;
          } catch (error) {
            return {error}
          }

  }




   }
}
</script>

<style scoped>

</style>