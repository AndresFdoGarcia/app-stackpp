<template>
<div id="User">
<h2>Hola <span> {{username}}, </span> ¡Bienvenido!</h2>
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
justify-content: center;
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
</style>