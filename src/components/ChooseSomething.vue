<template>
  <div id="chooseSomething">
        <h1>List Course</h1>
        <input type="text" v-model="newCourse" @keydown.enter="NewCourse">
        <button @click="NewCourse" ref="click">Click Here</button>
        <div v-for="(course,key) in courses " v-bind:key="key" >
          <span @click="course.status= !course.status" :class="{choose : course.status}">{{course.name}}</span>
        </div>
        <form action="" @keydown.enter.prevent="" @submit.prevent="" >
          <input type="text">
          <button type="submit">Submit</button>
        </form>
        <div id="parent" @mousemove="Parent">
          <div id="son" @mousemove.stop="Son">

          </div>
        </div>


  </div>
</template>

<script>
export default {
  name : "ChooseSomething",
  data(){
    return{
      courses : [
          {name:"node js",status:false},
          {name:"react js",status: true},
          {name:"javascript",status: false},
          {name:"vue js",status: true}
      ],
      newCourse : "",
    }
  },
  methods : {
      NewCourse : function (){
          this.courses.push(this.newCourse);
      },
      Parent:function (e){
        console.log('parent '+e.pageX)
      },
      Son:function (e){
      console.log('son '+e.pageX)
      }
  },
  filters:{

  }

}
</script>

<style scoped>
  .choose{
    background-color: blue;
  }
  #parent{
    height: 200px;
    width: 200px;
    position: relative;
    background-color: red;
  }
  #son{
    height: 50px;
    width: 50px;
    position: absolute;
    background-color: yellow;

  }
</style>