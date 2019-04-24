<template>
  <div class="cesta">
      <h1>Mi Cesta</h1>
      <div v-for="pr in listadoSelected" :key="pr.id" @click="getData()">
        <div>
            <img :src="pr.image" :alt="pr.titulo"/>
            <div class="titulo">{{pr.titulo}}</div>
            <div class="precio">{{pr.precio}}€</div>
        </div>
      </div>
      <div>
          <div class="titulo">TOTAL  <span>  ({{listadoSelected.length}} productos)</span></div>
          <div> {{ finalPrize }}€</div>
      </div>
  </div>
</template>

<script>

function isNotExist(array,precio){
        for(let i in array){
            if(array[i].precio == precio){
                return false;
            }
        }
        return true;
    }
export default {
    data(){
        return{
            productsSelected:[],
            precioTotal:[],
            finalPrize:0,
        }
    },
    props:['listadoSelected'],
    beforeUpdate(){
        const precioTotal2 = [];
        for(let index in this.listadoSelected){
            //se comprueba que en el array creado, no existe el mismo precio dos veces
            if(isNotExist(precioTotal2,this.listadoSelected[index].precio)){
                precioTotal2.push({
                    precio: this.listadoSelected[index].precio
                })
            }
        }
        //Se iguala el array con el array creado localmente
        this.precioTotal = precioTotal2;
    },
    updated(){
        let precio=0;
        for(let indexPrecio in this.precioTotal){
            precio += parseFloat(this.precioTotal[indexPrecio].precio);
        }
        this.finalPrize = precio;
    }
}
</script>

<style>
    .cesta{
        -webkit-box-shadow:0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
        box-shadow:0 10px 20px rgba(0,0,0,0.19), 0 6px 6px rgba(0,0,0,0.23);
    }
    .cesta > h1{
        margin: 0;
        font-size: 22px;
        line-height: 26px;
        color: #97be0d;
        font-weight: 400;
        border-bottom: 1px solid #97be0d;
        text-transform: uppercase;
        padding: 20px 0 20px 10px;
    }
    .cesta > div{
        display:none;
    }
    .cesta > div:last-of-type{
        display:flex;
    }
    .cesta > div > div:first-of-type{
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-align: center;
        -ms-flex-align: center;
        align-items: center;
        padding: 10px;
        margin: 0;
        width: 100%;
        border-bottom: 1px solid #cccc;
    }
    .cesta > div > div > img{width:80px;border:1px solid #cccccc;display:none;}
    .cesta > div > div > .titulo{min-width: 300px;width:100%;margin-left:20px;}
    .cesta > div > div > .precio{font-weight: bold}
    .cesta > div:last-of-type{
        display: -webkit-box;
        display: -ms-flexbox;
        display: flex;
        -webkit-box-align: center;
        -ms-flex-align: center;
        align-items: center;
    }
    .cesta > div:last-of-type > div{
        border:none;
    }
    .cesta > div:last-of-type > .titulo{
        font-size:25px;
        line-height:29px;
        font-weight:400;
        width:75%;
    }
    .cesta > div:last-of-type > .titulo > span{
        font-size:18px;
        line-height:24px;
        margin-left:30px;
    }
    .cesta > div:last-of-type > div:last-of-type{
        padding: 10px;
        margin: 0 10px;
        text-align:right;
        font-size:25px;
        line-height:29px;
        font-weight:bold;
    }

    @media (min-width: 601px) {
        .cesta > div{
            display:flex;
        }
        .cesta > div > div > img{
            display:block;
        }
        .cesta > h1{
            padding: 20px 0 20px 40px;
            font-size:32px;
            line-height:36px;
        }
        .cesta > div > div:first-of-type{
            padding: 20px;
            margin: 0 20px;
        }
        .cesta > div:last-of-type > div{
            width:50%;
        }
        .cesta > div:last-of-type > div:last-of-type{
            padding:20px;
            margin: 0 10px;
        }
    }
</style>
