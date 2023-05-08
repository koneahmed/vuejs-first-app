<template>
  <div id="app">
    <ToDos v-bind:todoEntries="todoEntries"/>
    
    <AddToDoButton @add-todo-event="addToDoItem"/>
  </div>
</template>

<script>
    import ToDos from './components/ToDos.vue'
    import AddToDoButton from './components/AddToDoButton.vue'

    export default {
    name: 'App',
    components: {
    ToDos
    },
    data() {
        return {
            todoEntries: [
                {
                    id: 1,
                    title: 'Infos sammeln',
                    completed: false
                },
                {
                    id: 2,
                    title: 'Test Projekt erstellen',
                    completed: false
                },
                {
                    id: 3,
                    title: 'Blog Beitrag schreiben',
                    completed: false
                },
                ],
            }
        },

        methods: {
          addToDoItem(newToDoItem) {
            this.todoEntries = [...this.todoEntries, newToDoItem];
          },
          deleteToDoItem(toDoId){
          this.todoEntries = this.todoEntries.filter(item => item.id !== toDoId)
          }

        },
    }
</script>

