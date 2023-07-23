<template>
    <div>
      <div class="item">
        <p><b>Nowe do zrobienia {{ newItem }}</b></p>
        <input type="text" placeholder="do zrobienia" v-model="newItem"> 
        <button @click="addItem">Dodaj</button>
      </div>
     <TodoItem  v-for="item in items" v-bind:key="item.id" v-bind:item="item" @removeClicked = "removeItem"/>
    </div>
    </template>
    
    <script>
    import TodoItem from "./TodoItem.vue"
    export default {
        components: {
            TodoItem
        },
        data() {
        return {
          newItem: '',
          items: [
            {title: 'Zrobić zakupy', completed: false, id: 1},
            {title: 'Wynieść śmieci', completed: false, id: 2}
          ]
        }
      },
      methods:{
        addItem(){
          this.items.push({
            title: this.newItem, 
            completed: false, 
            id: Math.random
          })
            this.newItem = ''
        },
        removeItem(id){
          const index = this.items.findIndex(el => el.id === id);
          this.items[index].completed = true;
        }
      }
    }
    </script>
    
    <style>
      button{
        background-color: darkgreen;
        color: white;
      }
      button:hover{
        background-color:rgb(4, 134, 4);
      }
      .item{
        border: 2px solid #cdcdcd;
        border-radius: 20px;
        text-align: center;
        margin: 8px;
        padding: 10px;
      }
      .completed{
        opacity: 0.5;
      }
      .completed h2{
        text-decoration: line-through;
      }
    </style>
    
    