// Task: 

// add new 'todos': done
// ability to delete a todo: done
// ability to move a todo up or down: done
// onclick add and remove line-through: didn't finish (commented the code out)

<template>
  <div class='toDoList'>
    <div>{{Heading}}</div>
    <input v-model="txtInput" type="text" v-on:keyup.enter="pressEnter">
    <ul>
        <!-- <li v-bind:key="index" v-on:click="filter" v-bind:class="{ active: isActive }" v-for="(todo, index) in todos"> -->
        <li v-bind:key="index" v-for="(todo, index) in todos">
                {{todo.title}}: {{todo.description}}
                <button v-on:click="moveUp(index)">move up</button>
                <button v-on:click="moveDown(index)">move down</button>
                <button v-on:click="deleteToDo(index)">delete</button>
        </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'toDoList',
  data() {
      return {
          txtInput: '',
          Heading: 'TO DO LIST',
          isActive: false,
          todos: [{
              title: 'new todo',
              description: 'iron clothes',
              done: false
          }, {
              title: 'new todo',
              description: 'fold clothes',
              done: false
          }]
      }
  }, 
  methods: {
      pressEnter: function() {
        console.log(this.txtInput);
        let textInput = this.txtInput;
        this.todos.push({title: 'new todo', description: textInput, done: false})
        this.txtInput = '';
      },
      deleteToDo: function(index) {
        this.todos.splice(index, 1);
      },
      moveUp: function(index) {
        console.log(index);
        if(index > 0) {
        this.todos.splice(index - 1, 0, this.todos[index]);
        this.todos.splice(index + 1, 1);
        }
      },
      moveDown: function(index) {
        console.log('down ' + index);
        if(index < this.todos.length - 1) {
        const temp = this.todos[index];
        this.todos.splice(index, 1);
        this.todos.splice(index + 1, 0, temp);            
        }
      },
      filter: function() {
        this.isActive = !this.isActive;
      }
  },
  computed: {
//   crossOut: function() {
//       var chosenClass = 'classA';
//       if(this.cross === false) {
//           chosenClass = 'classB'
//       }
//       return chosenClass;
//   }
  }
}
</script>

<style>
    /* .classA {text-decoration: line-through}
    .classB {text-decoration: none} */
</style>

