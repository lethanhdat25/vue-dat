<template>
  <div id="lap01">
    <input type="text" v-model="newTask">
    <button type="button" @click="addTask">Add</button>
    <div v-for="(task,index) in tasks" v-bind:key="index">
      <span :class="{done:task.status}">{{ task.content }}</span>
      <input type="checkbox" v-model="task.status">
    </div>
  </div>
</template>

<script>
export default {
  name: "Lap01",
  data() {
    return {
      newTask: "",
      tasks: []
    }
  },
  methods: {
    addTask: function () {
      this.tasks.push({content: this.newTask, status: false})
    }
  },
  watch: {
    newTask: function (newValue, oldValue) {
      console.log(oldValue + " change " + newValue)
    }
  }
}
</script>

<style scoped>
.done {
  text-decoration: line-through;
}
</style>