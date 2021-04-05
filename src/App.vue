<template>
  <div id="app">
    <img src="/img/tenor.gif" alt="" >
    <form v-on:submit.prevent="saveNewTask">
      <label for="new-task"></label>
      <input type="text" id="new-task" v-model="newTask">
      <input type="radio" id="High" name="Priority" value="High" checked v-model="picked">
      <label for="High" id="labelHigh">HIGH</label>
      <input type="radio" id="Low" name="Priority" value="Low" v-model="picked">
      <label for="Low" id="labelLow">LOW</label>
      <input type="submit" value="Save Task" id="submit">
    </form>
    <ul>
      <li v-for="task, index in todos" v-bind:key="index" v-bind:class="task.priority === 'High' ? 'high' : 'low'">
        {{task.name}}
      </li>
    </ul>
  </div>
</template>

<script>


export default {
  name: 'App',
  data() {
    return {
      todos: [
        {name: "Buy Shopping", priority: "High"},
        {name: "Clean Bathroom", priority:"Low"},
        {name: "Car's MOT", priority:"High"}
      ],
      newTask: "",
      picked: "High"
    }
  },
  methods: {
    saveNewTask: function() {
      if (this.newTask === "") {
        return
      }
      this.todos.push(
        {name: this.newTask, priority: this.picked});
        console.log("The task is", this.picked)
      
      this.newTask = "";
    }
  }
}
</script>

<style>
body{
  background-color: black;
}

#app {
  font-family: 'Press Start 2P', cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color:white;
  margin-top: 20px;
}

ul {
  list-style: none;
}

.high{
  color:red;
}

.low{
  color:greenyellow;
}

#submit {
  font-family: 'Press Start 2P', cursive;
  border: 4px white solid;
  background-color: darkgrey;
  margin-left: 10px;
  padding: 5px;
  
}

#new-task {
  font-family: 'Press Start 2P', cursive;
  border: 4px white solid;
  background-color: black;
  color: white;
  width: 155px;
  padding: 5px;
  margin-left: 20px;
}

ul {
  margin-top: 30px;
}

li {
  padding:10px;
  border: 2px white solid;
  width: 500px;
  margin-left: auto;
  margin-right:auto;
  margin-bottom:10px;
}

#High {
  margin-left: 10px;
}
label {
  margin-right: 12px;
  margin-left: 5px;
}

img {
  
  padding-left:50px;
  margin-bottom: 20px;
}

#labelHigh {
  color: red
}

#labelLow {
  color: greenyellow
}

#High, #Low {
  -webkit-appearance: none;
  -moz-appearance: none;
  appearance: none;

  width: 16px;
  height: 16px;
  border: 3px solid white;
  margin-right: 5px;

}

#High:checked {
  background-color: white

}

#Low:checked {
  background-color: white

}
</style>
