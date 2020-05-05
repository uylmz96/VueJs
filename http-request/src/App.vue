<template>
  <div id="container">
    <div class="row">
      <div class="col-md-8 offset-md-2 text-center">
        <h3 class="mt-5">TODO List | VueJs</h3>
        <hr />
        <div class="row">
          <div
            class="col-md-6 offset-md-3 d-flex justify-content-between flex-row align-items-center pt-2 pb-2"
          >
            <input type="text" v-model="todoText" />
            <button @click="addTodo()" class="btn btn-primary">Ekle</button>
          </div>
        </div>
        <hr />
        <div class="todo-container">
          <todo @deleteTodo="deleteTodo($event)" v-for="todo in todoList" :key="todo.id" :todo="todo" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import todo from "@/components/todo";
import axios from "axios";
export default {
  components: {
    todo
  },
  data() {
    return {
      todoList: [],
      todoText: ""
    };
  },
  methods: {
    addTodo() {
      axios
        .post("https://vuejs-httprequest.firebaseio.com/todos.json", {
          text: this.todoText
        })
        .then(response => {
          this.todoList.push({
            id: response.data.name,
            text: this.todoText
          });
        })
        .catch(x => {
          console.log(x);
        });
    },
    deleteTodo(todoID) {
      axios
        .delete("https://vuejs-httprequest.firebaseio.com/todos/"+todoID+".json")
        .then(response => {
            console.log(response)
            let index=this.todoList.findIndex(i=>{
              return i.id==todoID
            })
            this.todoList.splice(index,1)
        })
        .catch(x => {
          console.log(x);
        });
    }
  },
  created() {
    axios
      .get("https://vuejs-httprequest.firebaseio.com/todos.json")
      .then(response => {
        for (let key in response.data) {
          let todo = {
            text: response.data[key].text,
            id: key
          };
          this.todoList.push(todo);
        }
      })
      .catch(x => {
        console.log(x);
      });
  }
};
</script>

<style>
</style>
