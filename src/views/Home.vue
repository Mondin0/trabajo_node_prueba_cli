<template>
  <div class="home">
    <Header/>
    <div class="container-fluid">
      <button class="btn btn-primary" v-on:click="nuevo()">Nuevo paciente</button> <br>
      <table class="table table-hover">
        <thead>
          <tr>
            <th scope="col">ID</th>
            <th scope="col">NAME</th>
            <th scope="col">LASTNAME</th>
            <th scope="col">EMAIL</th>
            <th scope="col">PHONE</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="usuarios in Listausuarios" :key="usuarios.json_id" v-on:click="editar(usuarios.json_id)">
            <th scope="row">{{usuarios.json_id}}</th>
            <td>{{usuarios.name}}</td>
            <td>{{usuarios.lastname}}</td>
            <td>{{usuarios.email}}</td>
            <td>{{usuarios.phone}}</td>
          </tr>
        </tbody>
      </table>
    </div>
    <Footer/>
  </div>
</template>

<script>
// @ is an alias to /src
import axios from 'axios';
import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';


export default {
  name: 'Home',
  data(){
    return{
      Listausuarios: null
    }
  },
  components: {
    Header,
    Footer
  },
  mounted:function(){
    let direccion = "http://localhost:3000/api/usuarios";
    axios.get(direccion).then(data =>{
      console.log(data);
      this.Listausuarios= data.data;
    })
  },
  methods: {
    editar(json_id){
      this.$router.push('/editar/'+ json_id);
    },
    nuevo(){
      this.$router.push('/nuevo')
    }
  }
}
</script>

<style scoped>

</style>