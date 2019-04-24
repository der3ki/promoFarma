<template>
  <div>
    <nav-header></nav-header>
    <main>

      <listado-producto @productosSeleccionados="productSelected = $event"></listado-producto>
      <cesta :listadoSelected="productSelected"></cesta>
    </main>
  </div>
</template>

<script>
import Header from './components/navbar/header.vue'
import ListadoProductos from './components/listado/listado.vue'
import MiCesta from './components/cesta/micesta.vue'


export default {
  name: 'app',
  components: {
    navHeader:Header,
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
}
main{
  display:-webkit-box;
  display:-ms-flexbox;
  display:flex;
  max-width: 1200px;
  margin:0 auto;
}
main > ul,main> div{
  width:50%;
}

</style>
