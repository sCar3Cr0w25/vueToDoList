<template>
  <div>
    <h2>Todo List</h2>
    <div>
      <input type="text" v-model="task" />
      <button @click="submit">
        Add
      </button>
      <div v-for="task in tasks" :key="task.id" >
        <input type=checkbox  @click="toggleDone(task)" >
        <span :class="{ done: task.done }">{{task.name }}</span>
      </div>
      <button @click="removeAll()">clear</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "TodoApp",
  data() {
    return {
      task: "",
      tasks: [
        
      ],
    };
  },
  methods: {
    submit() {
      if (this.task.length === 0 ) {return}
      this.tasks.push({
        name: this.task,
        id: this.tasks.length + 1,
        done: false,
      });
      this.task = "";
    },
    toggleDone(task) {
      task.done = !task.done;
    },
    removeAll(){
      this.tasks = []
    },
  },
};
</script>

<style>
.done {
  text-decoration: line-through;
}
</style>