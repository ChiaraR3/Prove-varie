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
          <li v-for="(todo,index) in todos" 
           v-bind:key="todo.id"
           v-bind:title="todo.task"><label><input type="checkbox"><span>
          {{todo.task}}
            <button @click="deleteTodo">x</button></span></label></li>
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
    background-color:#ffb6c1;
    font-family:'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    text-align:center;
}
h1 {
    margin-top: 30px;
    background-color: #ffb6c1;
    border-radius: 10px;
    border-radius: 20% 5% 20% 5%/5% 20% 25% 20%;
    color:red;
}

ul{
   list-style:none;
}
input{  
    border: 0;
    border-bottom: 3px dashed red;
    background-color: transparent;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    font-size: 20px;
    padding: 10px 15px;
    width: 70%;
    color:#494a4b;
}
ul input{
    border: 0;
    background-color: transparent;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    font-size: 20px;
    padding: 15px;
    width: 5%;
    color:#494a4b;
}
button {
    margin-top: 6px;
    border: 3px solid hsl(198, 1%, 29%);
    border-radius: 8px;
    padding: 5px 10px;
    font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
    font-size: 20px;
}

span {
    margin: 50px 0 0 30px;
}
ul li {
    text-align: left;   
    margin: 10px 60px;
    font-size: 1.4rem;
    font-weight: 300;
    color: #494a4b;
}

   </style scoped>