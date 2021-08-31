<template>
    <div>
        <Header/>
        <div class="container">
            <form action="" class="form-horizontal">
                <div class="form-group left">
                    <label for="" class="control-label col-sm-2">Nombre</label>
                    <div class="col-sm-10">
                        <input type="text" name="name" class="form-control" id="name" v-model="form.name">
                    </div>
                </div>
                <div class="form-group left">
                    <label for="" class="control-label col-sm-2">Apellido</label>
                    <div class="col-sm-10">
                        <input type="text" name="lastname" class="form-control" id="lastname" v-model="form.lastname">
                    </div>
                </div>
                <div class="form-group left">
                    <label for="" class="control-label col-sm-2">Email</label>
                    <div class="col-sm-10">
                        <input type="text" name="email" class="form-control" id="email" v-model="form.email">
                    </div>
                </div>
                <div class="form-group left">
                    <label for="" class="control-label col-sm-2">Teléfono</label>
                    <div class="col-sm-10">
                        <input type="text" name="phone" class="form-control" id="phone" v-model="form.phone">
                    </div>
                </div>
                <div class="form-group">
                    <button type="button" class="btn btn-primary" v-on:click="editar()">Editar</button>
                    <!--<input type="submit" name="">-->
                    <button type="button" class="btn btn-danger margen" v-on:click="eliminar()">Eliminar</button>
                    <button type="button" class="btn btn-dark margen" v-on:click="salir()">Salir</button>
                </div>

            </form>
        </div>
        
        <Footer/>
    </div>
</template>

<script>

import Header from '@/components/Header.vue';
import Footer from '@/components/Footer.vue';
import axios from 'axios';

export default {
    name: "Editar",
    components: {
        Header,
        Footer
    },
    data:function(){
        return{
            form:{
                "name":"",
                "lastname":"",
                "email":"",
                "phone":""
            }
        }
    },
    methods:{
        editar(){
            //let article = { "name": this.form.name, "lastname": this.form, "email": this.form.email, "phone": this.form.phone};
            let article= this.form
            const articulo = JSON.stringify(article);
            
            axios.put("http://localhost:3000/api/usuarios/"+this.json_id, articulo).then(response => 
            this.setState({ updatedAt: response.data.updatedAt }))
            
        },
        salir(){
            this.$router.push("/");
        },
        eliminar(){
            axios.delete("http://localhost:3000/api/usuarios/"+ this.form.json_id);
            this.$router.push("/");
        }
    },
    mounted:function(){
        this.form.json_id = this.$route.params.json_id;
        axios.get("http://localhost:3000/api/usuarios/"+ this.form.json_id).then(datos =>{
            this.form.name=datos.data.name;
            this.form.lastname=datos.data.lastname;
            this.form.email=datos.data.email;
            this.form.phone=datos.data.phone;
            this.form.json_id=datos.data.json_id;
            console.log(this.form);
        })
    }
}
</script>

<style scoped>
    .left{
        text-align:left;


    }
</style>
