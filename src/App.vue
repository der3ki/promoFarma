<template>
  <div>
    <main>
      <listado-producto @productosSeleccionados="productSelected = $event"></listado-producto>
      <cesta :listadoSelected="productSelected"></cesta>
    </main>
  </div>
</template>

<script>
import ListadoProductos from './components/listado/listado.vue'
import MiCesta from './components/cesta/micesta.vue'


export default {
  name: 'app',
  components: {
    listadoProducto:ListadoProductos,
    cesta:MiCesta    
  },
  data(){
    return{
      productSelected: []
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Open+Sans:300,400,600,700,800');
body{
  font-size:15px;
  line-height: 19px;
  font-family: 'Open Sans', sans-serif;
  color:#333333;
  margin:0;
  -webkit-box-sizing:border-box;
  box-sizing:border-box;
}
main{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  max-width: 1200px;
  margin:0 auto;
  -webkit-box-pack:center;
  -ms-flex-pack:center;
  justify-content:center;
  -ms-flex-wrap:wrap;
  flex-wrap:wrap
}
main > ul,main> div{
  width:100%;
}
@media(min-width:601px){
  main{
    -webkit-box-pack:center;
    -ms-flex-pack:center;
    justify-content:center;
    -ms-flex-wrap:wrap;
    flex-wrap:wrap
  }
  main > ul, main > div{
    min-width:600px;
    width:50%;
  }
}
</style>
