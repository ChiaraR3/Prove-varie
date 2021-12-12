<template>
 <div id="todolist">
      <div class="header">
         <h1 :title="header">
            {{ header.toLocaleUpperCase() }}
         </h1>  
         <button v-if="state === 'default'" class="btn btn-primary" @click="changeState('edit')">Add</button>
         <button v-else class="btn btn-primary" @click="changeState('default')">Delete</button>
      </div>
      <div v-if="state === 'edit'" class="add-to-do">
         <input v-model="newTodo" type="text" placeholder="Add to do" @keyup.enter="saveTodo">
         <button class="btn btn-primary" @click="saveTodo">Save it</button>
      </div>
          <ul>
          <li v-for="todo in todos">{{ todo }}</li>
          </ul>
          <p v-if="todos.length === 0">Hai fatto tutto quello che dovevi</p>
   </div>
</template>


<script>
export default {
    data(){
        return{
    state: "default",
    header: "Otra to do list",
    newTodo: " ",
    todos: [
      "Comprar",
      "Estudiar",
      "Trabajar",
    ]
  }},
  methods:{
    saveTodo: function(){
      this.todos.push(this.newTodo);
      this.newTodo= "";
    },
    changeState: function(newState){
      this.state=newState;
      this.newTodo="";
    }}}
   </script>  