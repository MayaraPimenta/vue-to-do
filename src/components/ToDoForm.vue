<template>
  <div class="to-do-form">
    <h2 class="title">ToDo List</h2>
    <div class="main-input">
      <input type="text" placeholder="New Task..." v-model="newTask" required />
      <button @click="pushTask">Add</button>
    </div>
    <div class="list-container">
      <ul>
        <div class="task-container">
          <li v-for="task in tasks" :key="task" class="task-list">
            <input type="checkbox" name="task" id="task" v-model="task.done" />
            <span :class="{ done: task.done }">{{ task.title }}</span>
            <button @click="removeTask(task)">Delete</button>
          </li>
        </div>
      </ul>
    </div>
    <div class="buttons" v-show="tasks.length > 0">
      <button @click="removeAll">Remove All</button>
      <button @click="allDone">Mark All Done</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ToDo",

  data() {
    return {
      newTask: "",
      tasks: [],
    };
  },

  methods: {
    pushTask() {
      this.tasks.push({
        title: this.newTask,
        done: false,
      });
      this.newTask = "";
    },

    removeTask(task) {
      let taskIndex = this.tasks.indexOf(task);
      this.tasks.splice(taskIndex, 1);
    },

    allDone() {
      this.tasks.forEach((task) => {
        task.done = true;
      });
    },

    removeAll() {
      this.tasks = [];
    },
  },
};
</script>

<style scoped>
.done {
  text-decoration: line-through;
}

.to-do-form {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.title {
  color: rgb(59, 59, 59);
  display: flex;
  justify-content: center;
}

.main-input {
  display: flex;
  align-items: center;
  justify-content: center;
}

.main-input input {
  width: 24rem;
  height: 3rem;
  border: none;
  border-radius: 0.3rem 0 0 0.3rem;
  padding-left: 1rem;
  background-color: rgba(255, 255, 255, 0.726);
}

button {
  width: 6rem;
  height: 3.1rem;
  border: none;
  border-radius: 0 0.3rem 0.3rem 0;
  background-color: #f8f8f8bd;
  cursor: pointer;
}

button:hover {
  filter: brightness(1.5);
  transition: 0.4s;
}

.list-container {
  display: flex;
  justify-content: center;
}

ul {
  list-style: none;
  padding: 0;
  margin-top: 0;
}

.task-container {
  display: flex;
  flex-direction: column;
}

li {
  display: grid;
  grid-template-columns: 10% 70% 20%;
  align-items: center;
  background: #ffffff40;
  backdrop-filter: blur(1px);
  border-radius: 0.3rem;
  width: 31rem;
  transition: linear 1s ;
}

.task-list button {
  position: relative;
  right: -0.3rem;
  background-color: #ffffff5e;
}

.buttons {
  display: flex;
  width: 31rem;
  justify-content: space-between;
}

.buttons button {
  background: #ffffff40;
  backdrop-filter: blur(1px);
  border-radius: 0.3rem;
}
</style>
