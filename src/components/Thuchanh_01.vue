<template>
  <div id="this_root">
    <div id="shownGioHang">
      <div id="Giohang">Giỏ hàng ({{getCartQty}})</div>
    </div>
    <div id="shown-product">
        <div id="img-product">
          <img :src="data[0].color[data[0].selectedProduct].image">
        </div>
        <div id="detail-product">
          <h2>Màu sắc: {{getProduct.color_name}}</h2>
          <h3 v-if="getProduct.qty>0">Còn lại: {{getProduct.qty}}</h3>
          <h3 v-else>Sản phẩm hết hàng</h3>
          <h5 style="text-decoration: line-through"> {{formatOriginalPrice}}</h5>
          <small>{{data[0].discount*100}}%</small>
          <h4>Giá sản phẩm: {{formatFinalPrice}}</h4>

        </div>
        <div id="listColorImage">
          <div class="colorImage"
               :class="classActive(index)"
               v-for="(product,index) in data[0].color" :key="index" style="width: 100px;height: 100px"
               @click="data[0].selectedProduct=index">
            <img :src="product.image" style="width: 100%;height:100%;object-fit: cover">
          </div>
        </div>
      </div>
    <button id="addToCart" @click="handleAddToCart(data[0].selectedProduct)">
      Add To Cart
    </button>
    <button @click="clickChange">
      clisd
    </button>
  </div>
</template>

<script>
export default {
  name: "thuchanh_01",
  props:["data","setData"],
  data(){
    return{

    }
  },
  methods:{
    clickChange(){
        let data="dat";
        this.$emit('addData',data)
    },
    classActive(id){
      return{
        active : this.data[0].selectedProduct===id
      }
    },
    handleAddToCart(id){
      if (this.data[0].color[id].cart_color_qty+1>this.data[0].color[id].qty){
        alert("Không đủ sản phẩm");
      }else this.data[0].color[id].cart_color_qty++;
    },
  },
  computed: {
    formatOriginalPrice(){
      const price=this.data[0].price;
      return new Intl.NumberFormat('vn-VN', { style: 'currency', currency: 'VND' }).format(price);
    },
    formatFinalPrice(){
      const price=this.data[0].price-this.data[0].discount*this.data[0].price;
      return new Intl.NumberFormat('vn-VN', { style: 'currency', currency: 'VND' }).format(price);
    },
    getProduct(){
      const id=this.data[0].selectedProduct;
      return this.data[0].color[id]
    },
    getCartQty(){
      let cartQty=0;
      this.data[0].color.forEach(item=>cartQty+=item.cart_color_qty);
      return cartQty;
    }
  }
}
</script>

<style scoped>
  #listColorImage{
    display: flex;
    justify-content: center;
  }
  .colorImage{
    margin: 10px;
  }
  .active{
    border:1px solid red;
  }
</style>