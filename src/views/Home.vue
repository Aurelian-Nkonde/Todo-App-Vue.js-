<template>
  <div id="app">
    <div class="container mt-10 px-5 mx-auto">
      <div class="max-w-2xl mx-auto">

        <div class="max-w-sm mx-auto">
          <form @submit.prevent="AddTodo">
            <input type="text" v-model="newTodo" placeholder="Add a todo" class="w-full py-2 px-4 font-sans text-lg bg-gray-300 shadow-lg
             border-b-2 border-transparent transition ease-in-out duration-200 hover:border-red-500 outline-none ">
          </form>
        </div>

        <div class="mt-8 mb-6">
          <div class="flex justify-around items-center">
            <div class="flex items-center">
              <div class="flex flex-col">
                <div class="flex items-center">
                  <input type="checkbox" @change="markAll">
                  <p class="ml-2 text-lg">Check all</p>
                </div>
                <div class="flex items-center">
                  <input type="checkbox" @change="unmarkAll">
                  <p class="ml-2 text-lg">uncheck all</p>
                </div>
              </div>
            </div>
            <div class="">
              <h2 class="text-lg font-extrabold">{{ doneTodos }} todo's left</h2>
            </div>
          </div>
        </div>

        <div class="max-w-xl mx-auto">
          <div class="" v-if="todos.length > 0">
            <div class="" v-for="(todo, index) in todos" :key="todo.id">
              <div class="grid items-center grid-cols-2 mb-2 ">
                <div class="flex items-center overflow-hidden">
                  <input type="checkbox" v-model="todo.completed">
                  <h1 :class="{done: todo.completed}" class="ml-2 font-sans text-lg font-bold">{{ todo.title }}</h1>
                </div>
                <div class="flex justify-between">
                  <div class=""></div>
                  <div class="">
                      <button @click="deleteTodo(index)" class="font-sans text-base bg-red-600 transition ease-in-out duration-200 hover:bg-red-700 py-1 text-white capitalize px-7">delete</button>
                  </div>
                </div>
              </div>
            </div>
          </div>
          <div class="" v-else>
            <h1 class="font-sans text-center text-4xl mt-10 text-red-600 font-bold">No todos now !</h1>
          </div>
        </div>

      </div>
    </div>

  </div>
</template>

<script>
export default {
  name: "App",
  components: {

  },
  data(){
    return{
      header: "que_todo",
      idTodo: 1,
      newTodo: "",
      todos: [
        {id: 0, title: "Welcome to Que_todo", completed: false},
      ]
    }
  },
  methods: {
    AddTodo(){
      if (this.newTodo.trim().length < 1){
        return ""
      } else {
        this.todos.push({
        id: this.idTodo,
        title: this.newTodo,
        completed: false
      })
      this.newTodo = "";
      this.idTodo++
      }
    },
    deleteTodo(index){
      this.todos.splice(index, 1)
    },
    done(){
      this.todos.completed == !this.todos.completed
    },
    markAll(){
      this.todos.forEach(todo => todo.completed = true)
    },
    unmarkAll(){
      this.todos.forEach(todo => todo.completed = false)
    }
  },
  computed: {
    doneTodos(){
      return this.todos.filter(todo => todo.completed != true).length
    }
  }

}; 
</script>

<style >
  .done{
    color: red;
    text-decoration: line-through;
  }
</style>>