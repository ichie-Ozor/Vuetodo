<template>
<div>
  <div class="todo">
    <h1>Todo App</h1>
    <input type="text"  v-model="todo" placeholder="Enter todo here" />
    <button @click="addTodo">Click</button>
  </div>

  <div v-for="todoItem in todoList" :key="todoItem" class="item">
    <div class="itemList">{{todoItem}}</div>
    <button @click="editItem(todoItem)">Edit</button>
    <button @click="deleteItem(todoItem)">Delete</button>
  </div>
 </div>
</template>

<script>
export default {
  data(){
    return{ 
      todo: '',
      todoList: []
    }
  },
  methods: {
    addTodo(){
      this.todoList.push(this.todo)
      console.log(this.todoList)
      this.todo = ''
    },
    deleteItem(todoItem){
      this.todoList = this.todoList.filter((item) => {
        return todoItem !== item
      } )
    },
    editItem(todoItem){
      this.todo = this.todoList.find((item) => {
        return todoItem === item
      })
      this.deleteItem(todoItem)
    }
  }
}
</script>

<style>
todo{
    max-width: 420px;
    margin: 30px auto;
    background: rgb(233, 218, 218);
    text-align: left;
    padding: 40px;
    border-radius: 10px;
}
input{
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555;
}
button {
  background: #0faf87;
  color: white;
  height: 40px;
  border: none;
  padding: 8px 16px;
  border-radius: 4px;
  font-size: 16px;
  letter-spacing: 1px;
  cursor: pointer;
  margin: 10px;
}
.item{
  position: relative;
  display: flex;
}
.itemList{
  position: relative;
  top: 9px;
  width: 200px;
  height: 40px;
  background: rgb(79, 73, 61);
  box-shadow: #675c5c;
  color: white;
  /* margin: 20px auto; */
  padding: auto 10px;
  align-items: center;
  font-size: 25px;
  font-weight: 20px;
  border-radius: 5px;
}
</style>