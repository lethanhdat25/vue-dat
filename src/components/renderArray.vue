<template>
  <div id="renderArray">
      <div v-for="(item,index) in arrNumber" :key="index">
          {{item}}
      </div>
  </div>
</template>

<script>
export default {
  name: "renderArray",
  data(){
    return{
      arrNumber:[1,2,3,4,5,6]
    }
  },
  computed:{
    findPrice(){
      return this.products.filter(item=>item.price>3000)
    }
  }
}
</script>

<style scoped>

</style>