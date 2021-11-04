<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Thuchanh_01 :data="product"  @addData="setData"/>
    {{freezeData()}}
 </div>
</template>

<script>
import Thuchanh_01 from "@/components/Thuchanh_01";
export default {
  name: 'App',
  components: {Thuchanh_01},
  data(){
    return{
      product:[
        {
          name:"ao 01",
          color:[
            {
              image:require("./assets/aoden01.jpg"),
              color_name:"black",
              qty:8,
              cart_color_qty:0
            },
            {
              image:require("./assets/aotrang01.jpg"),
              color_name:"white",
              qty:5,
              cart_color_qty:0,
            },
            {
              image:require("./assets/aohong01.jpg"),
              color_name:"pink",
              qty:0,
              cart_color_qty:0,
            },
          ],
          description:"day la ao thu 1",
          price:100000,
          discount:0.5,
          selectedProduct:0,
        }
      ]
    }
  },
  methods:{
    setData(name){
      this.product.push(name);
    },
    freezeData(){
      Object.freeze(this.product);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
