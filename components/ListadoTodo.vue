<template>
<body>
 <div id="todolist">
      <div class="header">
         <h1 :title="header">
            {{ header.toLocaleUpperCase() }}
         </h1>  
         <button v-if="state === 'default'" class="btn btn-primary" @click="changeState('edit')">Add new task</button>
         <button v-else class="btn btn-primary" @click="changeState('default')">Nothing more to do</button>
      </div>
      <div v-if="state === 'edit'" class="add-to-do">
         <input v-model="newTodo" type="text" placeholder="New one" @keyup.enter="saveTodo">
         <button class="btn btn-primary" @click="saveTodo">Put it in my list</button>
      </div>
          <ul>
          <div><li v-for="(todo,index) in todos" 
           v-bind:key="todo.id"
           v-bind:title="todo.task">
            {{ todo.id }}.{{todo.task}}
            <button @click="deleteTodo">x</button></li></div>
          </ul>
          <p v-if="todos.length === 0">Good job! Everything done!</p>
   </div>
   </body>
</template>


<script>
export default {
    data(){
        return{
    state: "default",
    header: "To do list",
    newTodo: " ",
    todos: [
      {
          id:1, 
          task: "Comprar"
      },
      {
          id:2,
          task: "Estudiar"
      },
      {
          id:3,
          task:"Trabajar"
      },
    ],
    nextTodoId: 4
  }},
  methods:{
    saveTodo: function(){
      this.todos.push({
          id: this.nextTodoId++,
          task: this.newTodo
      });
      this.newTodo= "";
    },
    changeState: function(newState){
      this.state=newState;
      this.newTodo="";
    },
    deleteTodo: function(todos,index){
        this.todos.splice(index,1);
        } 
    }}
   </script>  

   <style scoped>
body {
    background-color: #ffb6c1;
    font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    text-align: center;
}
h1 {
    color:red;
}
ul.div{
    border:black
}
   </style scoped>