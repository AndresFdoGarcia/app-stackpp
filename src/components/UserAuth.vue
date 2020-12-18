<template>
<div id="AuthUser" class="auth_user">
<div class="container_auth_user">
<h2>Autenticarse</h2>
<form v-on:submit.prevent="processAuthUser" >
<div class="form-group">
    <label for="username">Nombre de Usuario</label>
    <input type="text" class="form-control" id="username" v-model="form.username">
</div>
<div class="form-group">
    <label for="password">Contraseña</label>
    <input type="password" class="form-control" id="password"  v-model="form.password">
</div>
<div class="form-group">
    <button class="btn btn-primary">Validar</button>
</div>
</form>
</div>
</div>


</template>
<script>
import axios from 'axios';
export default {
name: "UserAuth",
data(){
    return {
        form: {
            username:'',
            password:'',
        }
    }
},
    methods: {
        
        processAuthUser: function(){
            
            console.log(this.form)
            axios.post("https://stackppapp.herokuapp.com/user/auth/", {"username":this.form.username,"password":this.form.password})
                .then((result) => {                   
                    alert("Autenticación Exitosa")
                    this.$emit('log-in',this.form.username)
                                        
                })
                .catch((error) => {
                    if (error.response.status == "404")
                        alert("ERROR 404: Usuario no encontrado.");
                    if (error.response.status == "403")
                        alert("ERROR 403: Contraseña Erronea.");                     
                }).finally(() => {
                     //Perform action in always
                });
        }
    }
}
</script>
<style>
.auth_user{
margin: 0;
padding: 0%;
height: 100%;
width: 100%;
display: flex;
justify-content: center;
align-items: center;
}
.container_auth_user {
border: 3px solid crimson;
border-radius: 10px;
width: 25%;
height: 60%;
display: flex;
flex-direction: column;
justify-content: center;
align-items: center;
}
.auth_user h2{
color: #24313f;
}
.auth_user form{
width: 50%;
}
.auth_user input{
height: 40px;
width: 100%;
box-sizing: border-box;
padding: 10px 20px;
margin: 5px 0;
border: 1px solid #283747;
}
.auth_user button{
width: 100%;
height: 40px;
color: #E5E7E9;
background: #283747;
border: 1px solid #E5E7E9;
border-radius: 5px;
padding: 10px 25px;
margin: 5px 0;
}
.auth_user button:hover{
color: #080808;
background:crimson;
border: 1px solid #283747;
}
</style>