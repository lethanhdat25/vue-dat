<template>
  <div id="computed_method">
      <span>Number + A={{addA}}</span>
      <span >Number + B={{addB}}</span>
      <button @click="a++">A++</button>
      <button @click="b++">B++</button>
  </div>
</template>

<script>
export default {
  name: "Computed_and_Method",
  data(){
    return{
      number:20,
      a:0,
      b:0
    }
  },
  methods: {},
    computed:{
      addA:function(){
        console.log("add A run");
        return this.a+this.number;
      },
      addB:function (){
        console.log("add B run");
        return this.b+this.number;
      },
    }
}
</script>

<style scoped>

</style>