<template>
  <div>
    <h1>Minha lista de tarefas!</h1>
    <button @click="handleShowHideList">Ver a lista</button>

    <br />
    <br />

    <input type="text" v-focus v-model="state.currentTask" @keyup.enter="addTask" />

    <ul v-if="state.showList">
      <li
        v-for="(task, index) in state.tasks"
        :key="`${task}-${index}`"
        :class="{
          'line-through': task.isDone,
        }"
        class="task-item"
        @dblclick="complete(task)"
      >
        {{ task.name }}
        <button @click="remove(task)">&times;</button>
      </li>
    </ul>

    <p v-else>Lista de tarefas escondidas</p>
  </div>
</template>

<script>
import {reactive} from 'vue'

const focus = {
  inserted: (el) => {
    el.focus();
  },
};

export default {
  directives: {
    focus
  },
  setup() {
    const state = reactive({
      currentTask: "",
      showList: false,
      tasks: [
        { name: "Make curse", isDone: false }
        ]
    })
    
    function handleShowHideList () {
      state.showList = !state.showList;
    }

    function complete (task) {
      state.tasks = state.tasks.map((t) => {
        if (t.name === task.name) {
          return { ...t, isDone: !t.isDone };
        }
        return { ...t };
      });
    }

    function addTask () {
      state.tasks.push({
        name: state.currentTask,
        isDone: false,
      });
      state.currentTask = "";
    }

    function remove (task) {
      state.tasks = state.tasks.filter((t) => t.name !== task.name);
    }

    return {
      state,
      handleShowHideList,
      complete,
      remove,
      addTask
    }
  }
}
</script>

<style scoped>
.line-through {
  text-decoration: line-through;
}

.task-item {
  cursor: pointer;
}
</style>