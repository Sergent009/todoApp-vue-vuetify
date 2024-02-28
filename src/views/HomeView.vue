<template>
  <div class="home pa-6">
  <div v-for="task in tasks" :key="task.id">
    <!-- p for padding, t for top, 0 is the size  -->
    <v-list flat class="pt-0">
      <v-list-item @click="doneTask(task.id)">
        <template v-slot:default>

          <v-list-item-action>
            <v-checkbox :input-value="task.done" color="primary"></v-checkbox>
          </v-list-item-action>

          <v-list-item-content>
            <v-list-item-title>{{task.title}}</v-list-item-title>
          </v-list-item-content>

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
      tasks: [
        {
          id: 1,
          title: 'Wake Up',
          done: false
        },
        {
          id: 2,
          title: 'Do some good deeds for Akhirah',
          done: false
        },
        {
          id: 3,
          title: 'Do some coding to earn money',
          done: false
        },
      ]
    }
  },

  methods: {
    doneTask(id){
      let task = this.tasks.filter(task => task.id === id)[0]
        task.done = !task.done
  }
}
}
</script>
