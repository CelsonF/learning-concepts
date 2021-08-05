<template>
  <div>
    <h1>Minha lista de tarefas!</h1>
    <button @click="handleShowHideList">Ver a lista</button>

    <br />
    <br />

    <input type="text" 
    v-focus 
    v-model="currentTask"
    @keyup.enter="addTask"
    />

    <ul v-if="showList">
      <li v-for="(task, index) in tasks" 
          :key="`${task}-${index}`"
          :class="{
            'line-through':task.isDone
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
const focus = {
  inserted: (el) => {
    el.focus();
  },
};

export default {
  directives: {
    focus,
  },
  data: () => ({
    currentTask:'',
    showList: false,
    tasks: [{ name: "Make curse", isDone: false }],
  }),
  methods: {
    handleShowHideList() {
      this.showList = !this.showList;
    },
    complete(task){
      this.tasks = this.tasks.map(t => {
        if (t.name === task.name) {
          return { ...t,isDone: !t.isDone}
        }
        return {...t}
      });
    },
    addTask() {
      this.tasks.push({
        name:this.currentTask,
        isDone:false
      })
      this.currentTask = '';
    }
    ,
    remove(task) {
      this.tasks = this.tasks.filter(t => t.name !== task.name)
    },
  },
};
</script>

<style scoped>
.line-through {
  text-decoration:line-through;
}

.task-item {
  cursor: pointer;
}

</style>