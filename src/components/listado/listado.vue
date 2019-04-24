<template>
  <ul class="listado">
      <li v-for="data in myJson" :key="data.id">
          <div class="listado">{{data.titulo}}</div>
          <div class="precio">{{data.precio}}€</div>
          <button @click="getData(data)" :disabled="productSelect.includes(data)" class="button"></button>
      </li>
  </ul>
</template>

<script>
import json from './listado.json'

export default {
    data(){
        return{
            myJson:json,
            productSelect: [],
        }
    },
    props: ['listadoSelected'],
    methods:{
        getData(event){
            this.productSelect.push(event);
            this.$emit('productosSeleccionados',this.productSelect);
        }
    }
    
}
</script>

<style>
    button{
            padding: 10px;
            width:100px;
            height: 50px;
            background-image: url('../../assets/add-to-cart.png');
            background-size: 50px;
            background-color: #97be0d;
            background-repeat: no-repeat;
            background-position: 25px;
            border: none;
            -webkit-transition: .3s all;
            -o-transition: .3s all;
            transition: .3s all;
    }
    ul{
        margin:0;
        padding:0;
    }
    ul.listado > li{
        display:-webkit-box;
        display:-ms-flexbox;
        display:flex;
        -webkit-box-align:center;
        -ms-flex-align:center;
        align-items:center;
        margin:20px 0;
    }
    ul.listado > li:first-of-type{
        margin-top:0;
    }
    ul.listado > li > div.listado{
        width:100%;
        max-width: 350px;;
    }
    ul.listado > li > div.precio{
        width:15%;
    }
    ul.listado > li > div.precio{
        font-size:19px;
        font-weight:bold;
        line-height: 19px;
    }
    ul.listado> li > button[disabled]{
        background-color: #cccccc;
    }
</style>
