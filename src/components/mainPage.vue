<template>
  <div>
    <h1>TODO-LIST</h1>
    <form @submit.prevent="addTodo" class="todoForm">
        <div class="todoFormSection">
            <label>New Todo</label>
            <div class="addTodoInput">
                <input v-model="newTodo" type="text" name="newTodo" placeholder="Add a new todo..." />
                <button>ADD TODO</button>
            </div>
        </div>
    </form>
    <hr />
    <div class="todoSection" v-for="(todo, index) in todos" :key="index">
        <div class="eachTodo">
            <div class="mainTodo">
                <input type="checkbox" v-model="todo.isChecked"/>
                <p class="todo" :class="{ todoChecked: todo.isChecked}">{{ todo.content }}</p>
            </div>
            <button @click="removeTodo(index)">remove</button>
        </div>
       
    </div>
  </div>

  <!-- <button @click="printConsole">Testing button</button> -->
</template>

<script setup>
import { ref } from 'vue';
const newTodo = ref('');
const todos = ref([]);
const addTodo =()=>{
    console.log(`Added ${newTodo.value}`)
    todos.value.push({
        done: false,
        content: newTodo.value,
        isChecked: false
    })
    newTodo.value = '';
}

const removeTodo = (index) =>{
    todos.value.splice(index, 1)
}

const printConsole =()=>{
    console.log(todos.isChecked)
}

</script>

<style scoped>
h1{
    font-size: 3rem;
    font-weight: 700;
    font-family:  'Times New Roman', serif;
    color: rgb(0, 0, 133);
    text-align: center;
}
.todoForm{
    display: flex;
    flex-direction: column;
    width: 100%;
}
.addTodoInput{
    width: 100%;
    display: flex;
    flex-direction: row;
    align-items: center;
    justify-content: space-between;
    max-width: 700px;
}

.todoForm label{
    color: rgb(0, 0, 133);
    font-size: 1.5rem;
    font-weight: 700;
}
.todoForm input{
    border: 2px rgb(0, 0, 133) solid;
    height: 30px;
    color: rgb(0, 0, 133);
    border-radius: 15px;
    width: 75%;
    padding-left: 10px;
}
.todoForm button{
    border-radius: 15px;
    color: white;
    font-weight: 700;
    padding: 0px 20px;
    width: 10rem;
    height: 36px;
    margin-left: 5px;
}
.todo{
  cursor: pointer;
    margin: 0 20px;
}

.todoChecked{
    text-decoration: line-through;
}
button{
    background-color: blue;
}

.todoSection{
    display: flex;
    flex-direction: row;
    justify-content: space-between;
    margin-bottom: 20px;
}

.mainTodo{
    display: flex;
    align-items: start;
   
}
.eachTodo{
    display: flex;
    justify-content: space-between;
    align-items: start;
    width: 100%;
    max-width: 700px;
}

.eachTodo button{
    padding: 10px 20px;
    border-radius: 15px;
    border: 1px;
    color: white;
    max-width: 10rem;
}

h4{
    font-weight: 400;
    margin-left: 15px;
    font-size: 20px;
    text-align: left;
}

</style>