<template>
  <div id="app">

    <SearchBar  v-on:keysearch-changed="handleKeySearchChanged"></SearchBar>
    <hr/>

    <TodoList
    v-bind:items="visibleTodos" 
    v-on:todo-deleted="handleTodoDeleted"
    v-on:todo-done="handleTodoDone" 
    ></TodoList>
    
    <hr/>
    <TodoAdd v-on:todo-added="handleTodoAdded"></TodoAdd>

  </div>
</template>

<script>
  import SearchBar from './components/SearchBar/SearchBar.vue'
  import TodoList from './components/TodoList/TodoList.vue'
  import TodoAdd from './components/TodoAdd/TodoAdd.vue'

  export default {
    name: 'App',
    components: {
      SearchBar,
      TodoList,
      TodoAdd
    },
    
    data: function(){
      return {
        todos: [
        {id: 1, title: 'tea2', isDone: false},
        {id: 2, title: 'milk', isDone: false},
        {id: 3, title: 'soda', isDone: false},
        ],
        keySearch: ''
      }
    },

    computed: {
      visibleTodos: function(){
        let newList = [...this.todos]
        let keySearch = this.keySearch

        newList = newList.filter(function(item){
          return item.title.toLowerCase().includes(keySearch.toLowerCase())
        })
        return newList
      }
    },

    methods: {
      handleTodoAdded: function(todoName){
        console.log('app receive: ', todoName)

        let todos = this.todos
        let newId = todos[todos.length - 1].id + 1
        todos.push({id: newId, title: todoName, isDone: false})
      },

      handleKeySearchChanged: function(keySearch){
        console.log('app receive: ', keySearch)
        this.keySearch = keySearch
      },

      handleTodoDeleted: function(todo){
        console.log('app receive: ', todo)

        let todos = this.todos
        let index = todos.indexOf(todo)
        todos.splice(index, 1)

      },

      handleTodoDone: function(todo){
        console.log('app receive: ', todo)

        let todos = this.todos
        let index = todos.indexOf(todo)
        todos[index].isDone = true
      }
    }
  }
</script>

<style>
body {
  background: #fff;
  color: #333;
  font-family: Lato, sans-serif;
}

.container {
  width: 400px;
  margin: 0 auto;
  margin-top: 100px;
}

h3 {
  color: #333;
  font-weight: bold;
  font-size: 25px;
  border-bottom: 2px solid #333;
  padding: 30px 0 3px 0;
  margin: 0 0 20px;
  text-transform: uppercase;
}

button {
  border-radius: 4px;
  color: white;
  min-width: 80px;
  text-align: center;
  text-decoration: none;
  display: inline-block;
  font-size: 10pt;
  cursor: pointer;
  background-color: white;
  color: black;
  border: 2px solid #008CBA;
  transition-duration: 0.2s;
  margin: 10px;
}

button:hover {
  background-color: #008CBA;
  color: white;
}

input[type='text'] {
  display: inline-block;
  width: 100%;
  font-size: 11pt;
  -webkit-transition: all 0.3s ease-in-out;
  -moz-transition: all 0.3s ease-in-out;
  -ms-transition: all 0.3s ease-in-out;
  -o-transition: all 0.3s ease-in-out;
  transition: all 0.3s ease-in-out;
  outline: none;
  padding: 7px 0px 7px 7px;
  margin: 5px 1px 3px 0px;
  border: 1px solid #dddddd;
  border-left: none;
  border-right: none;
  border-top: none;
}

input[type='text']:focus {
  box-shadow: 0 0 7px rgba(81, 203, 238, 1);
  border: 1px solid rgba(81, 203, 238, 1);
}

.fg {
  display: flex;
  justify-content: space-between;
}

.fg input {
  margin-right: 10px;
}

ul {
  margin: 0;
  padding: 0;
}

li {
  display: flex;
  justify-content: space-between;
  align-items: center;
  list-style: none;
  border-bottom: 1px solid #eee;
  font-size: 18px;
  line-height: 40px;
  padding-left: 20px;
}

li.done {
  text-decoration: line-through;
  color: green;

}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /*text-align: center;*/
  color: #2c3e50;
  max-width: 500px;
  margin: auto;
}



</style>
