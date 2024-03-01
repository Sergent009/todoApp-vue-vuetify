<template>
  <div class="home pa-6">
    <v-text-field outlined label="Add Task" append-icon="mdi-plus" hide-details clearable v-model="newTaskTitle" @click:append="addTask" @keyup.enter="addTask">
    </v-text-field>
  <div v-for="task in tasks" :key="task.id">
    <!-- p for padding, t for top, 0 is the size  -->
    <v-list flat class="pt-0">
      <v-list-item @click="doneTask(task.id)" :class="{'blue lighten-5': task.done}">
        <template v-slot:default>

          <v-list-item-action>
            <v-checkbox :input-value="task.done" color="primary"></v-checkbox>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title :class="{'text-decoration-line-through' : task.done}">{{task.title}}</v-list-item-title>
          </v-list-item-content>
        
          <v-list-item-action>
            <v-btn @click.stop="deleteTask(task.id)" icon>
              <v-icon color="primary lighten-1">mdi-delete</v-icon>
            </v-btn>
          </v-list-item-action>

        </template>
      </v-list-item>
      <v-divider></v-divider>
    </v-list>
  </div>
  </div>
</template>

<script>

export default {
  name: 'Home',
  data(){
    return{
      newTaskTitle: '',
      tasks: []
    }
  },

  methods: {
    doneTask(id){
      let task = this.tasks.filter(task => task.id === id)[0]
      task.done = !task.done
    },
    deleteTask(id){
      this.tasks = this.tasks.filter(task => task.id !== id)
    },

    addTask(){
      let newTask = {
        id: Date.now(),
        title: this.newTaskTitle,
        done: false
      }
      this.tasks.push(newTask)
      this.newTaskTitle = ''
    }
}
}
</script>
