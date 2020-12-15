<template>
    <div id="UserBalance">
        <h2> {{username}} </h2>
        <h2>Tu ingreso es: <span> {{valor}} COP</span></h2>
    </div>
</template>

<script> 
    import axios from'axios';
    export default {
        name: 'UserBalance',
        data: function(){
            return {username:"", descripcion: 0
            }
        },

        created: function(){
            this.username = this.$route.params.username
            let self = this
            axios.get("https://sprint2-api.herokuapp.com/ingreso/" + this.username)
                .then((result) => {
                    self.valor = result.data.valor
                })
                .catch((error) => {
                    alert("ERRORServidor");
                });
        }
    }                      
</script>    

<style>
#UserBalance{
    width:100%;
    height:100%;
    display:flex;
    flex-direction:column;
    justify-content:center;
    align-items:center;
}
#UserBalance h2{
    font-size:50px;
    color:#283747;
}

#UserBalance span{
    color:crimson;
    font-weight:bold;
}
</style>