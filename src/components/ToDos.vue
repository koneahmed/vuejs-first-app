<template>
    <div>
        <h1>Meine To-Do-Liste</h1>
        <ul>
            <li v-bind:key="item.id" v-for="item in todoEntries">
                <!-- <ToDoItem v-bind:todoItem="item" /> -->
                <ToDoItem v-bind:todoItem="item" @delete-todo-event="$emit('delete-todo-event', item.id)"/>

            </li>   
        </ul>
    </div>
</template>

<script>

import ToDoItem from "./ToDoItem.vue";

export default {
  name: 'ToDos',
  components: {
      ToDoItem
  },
  props: [
      "todoEntries"
  ],

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