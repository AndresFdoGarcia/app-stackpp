<template>
<div id="User">
<div class="d-flex justify-content-between">
<h2>Hola <span> {{username}}, </span> ¡Bienvenido!</h2><br>
<div class="fuente"><h3>Esta es una presentación realizada para ejemplificar el posible contenido de la aplicacion</h3></div>
</div>
<img src="../assets/portatil.png" height="470px" width="500px">
</div>
</template>
<script>
    export default {
        name: "User",
        data:function(){
            return {
                username: "",
                
            }
        },
        created: function(){
            this.username = this.$route.params.username
            
        }
}
</script>
<style>
#User{
width: 100%;
height: 100%;
display: flex;
justify-content: space-around;
align-items: center;
}
#User h2{
font-size: 50px;
color: #24313f;
}
#User span{
color: crimson;
font-weight: bold;
}
#User h3{
    width: 500px;
    background: rgba(0, 0, 0, 0.363);
    border: 1px solid #393939;
    border-radius: 5px 5px 5px 5px;
    color: #fffbfb;
    padding: 5px;

}
</style>