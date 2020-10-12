<template>
  <div id="app">
    <ul>
      <li v-for="(task, index) in tasks" :key="index" :class="task.Priority">
        <span>{{ task.name }}</span>


      </li>


    </ul>

    <form v-on:submit.prevent="saveNewTask">
      <label for="new-task">Add a new task</label>
      <input type="text" id="new-task" v-model="newTask.name" />
      <label for="priority">Priority:
      <label for="high-priority">High</label>
      <input type="radio" id="high-priority" name="priority" value="High" v-model="newTask.Priority" />
      <label for="low-priority">Low</label>
      <input type="radio" id="low-priority" name="priority" value="Low" v-model="newTask.Priority" /></label>
      <input type="submit" value="Save New Task">
    </form>
  </div>
</template>

<script>


export default {
  data(){
    return {
      tasks: [
        {name:"Buy shopping", Priority: "Low"},
        {name:"Clean bathroom", Priority: "Low"},
        {name:"Car's MOT", Priority: "High"},
      ],
      newTask: {
        name: "",
        Priority: null
      },
    }
  },
  methods: {
    saveNewTask: function () {
      this.tasks.push(this.newTask);
      this.newTask = {
        name: "",
        Priority: null
      }
    },
  },

};
</script>

<style>
#app {
  width: 60%;
  margin: 0 auto;
  font-family: 'Lato', sans-serif;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

li {
  margin: 20px 0;
  padding: 10px;
  display: flex;
  justify-content: space-between;
}

li span {
  padding: 8px;
}

li button {
  background: #f2360c;
  color: #fff;
  border: none;
  padding: 10px;
  cursor: pointer;
}

li.Low {
  border: 2px solid #1a681e;
}

li.High {
  border: 2px solid #f2360c;
}

input[type="text"] {
  padding: 10px;
  width: 50%;
  margin:5px;
}

button, input[type="submit"]{
  padding: 10px;
  background: #000;
  color: #fff;
  cursor: pointer;
  border: 1px solid #000;
}

</style>
