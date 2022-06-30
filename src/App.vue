<template>
    <div id="root">
      <div class="todo-container">
      <img id="logo" alt="logo" src="./assets/logo.png">
        <div class="todo-wrap">
          <HelloWorld />
          <myHeader @addTodo="addTodo"/>
          <!-- <myList :todos="todos" :checkTodo="checkTodo" :deleteTodo="deleteTodo"/> -->
          <myList :todos="todos" />
          <myFooter :todos="todos" @checkAllTodo="checkAllTodo" @clearAllTodo="clearAllTodo"/>
        </div>
              <img id="logo" alt="logo" src="./assets/chong.jpg">
      </div>
  </div>
</template>

<script>
// import pubsub from 'pubsub-js'
import myHeader from './components/myHeader.vue'
import myList from './components/myList.vue'
import myFooter from './components/myFooter.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    myHeader,myList,myFooter,HelloWorld
  },
  data() {
    return {
      todos:JSON.parse(localStorage.getItem('todos')) || []
    }
  },
  methods: {
    // 添加一个todo
    addTodo(todoObj){
      this.todos.unshift(todoObj)
    },
    // 勾选or取消勾选一个todo
    checkTodo(id){
      this.todos.forEach((todo)=>{
        if(todo.id === id) todo.done = !todo.done
      })
    },
    //改
    updateTodo(id,title){
      this.todos.forEach((todo)=>{
        if(todo.id === id) todo.title = title
      })
    },
    // 删除一个todo
    deleteTodo(id){
      this.todos=this.todos.filter(todo => todo.id !== id)
    },
    // 全选or全不选
    checkAllTodo(done){
      this.todos.forEach((todo)=>{
        todo.done = done
      })
    },
    //清除所有已经完成的todo
   clearAllTodo(){
      this.todos =  this.todos.filter((todo)=>{
        return !todo.done
      })
   }
  },
  watch:{
    todos:{
      deep:true,
      handler(value){
      localStorage.setItem('todos',JSON.stringify(value))
      }
    }
  },
  mounted(){
    this.$bus.$on('checkTodo',this.checkTodo)
    this.$bus.$on('updateTodo',this.updateTodo)
    this.$bus.$on('deleteTodo',this.deleteTodo)
    // this.pubId = pubsub.subscribe('deleteTodo',this.deleteTodo)
  },
  beforeDestroy(){
    this.$bus.$off(['checkTodo','deleteTodo','updateTodo'])
    // this.$bus.$off('checkTodo')
    // pubsub.unsubscribe(this.pubId)
  }
}
</script>

<style>
#root{
  background-image: url(./assets/bg.png);
  -webkit-background-size: cover;
  -o-background-size: cover;                
  background-size: cover;
  background-repeat:no-repeat;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#logo {
  width: 30%;
  height: 30%;
  margin-top: 5%;
}
.logo{
   height: auto; width: auto
}
  /*base*/
  body {
    background: #fff;
  }
  .btn {
    display: inline-block;
    padding: 4px 12px;
    margin-bottom: 0;
    font-size: 14px;
    line-height: 20px;
    text-align: center;
    vertical-align: middle;
    cursor: pointer;
    box-shadow: inset 0 1px 0 rgba(255, 255, 255, 0.2), 0 1px 2px rgba(0, 0, 0, 0.05);
    border-radius: 4px;
  }
  .btn-danger {
    color: #fff;
    background-color: #da4f49;
    border: 1px solid #bd362f;
  }
   .btn-edit {
    color: #fff;
    margin-right: 3px;
    background-color: skyblue;
    border: 1px solid skyblue;
  }
  .btn-danger:hover {
    color: #fff;
    background-color: #bd362f;
  }
  .btn:focus {
    outline: none;
  }
  .todo-container {
    width: 600px;
    margin: 0 auto;
    background-color:Bisque ;
    filter:alpha(Opacity=40);-moz-opacity:0.9;opacity: 0.9;
  }
  .todo-container .todo-wrap {
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 5px;
  }
</style>
