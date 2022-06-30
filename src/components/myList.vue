<template>
  <ul class="todo-main">
    <!-- <myItem v-for="todoObj in todos" :key="todoObj.id"  :todo="todoObj" :checkTodo="checkTodo" :deleteTodo="deleteTodo"/> -->
    <transition-group appear name="todo">
      <myItem v-for="todoObj in todos" :key="todoObj.id"  :todo="todoObj" />
    </transition-group>
    

  </ul>
</template>

<script>
import myItem from './myItem.vue'
export default {
    name:'myList',
    components:{
        myItem
    },
    // props:['todos','checkTodo','deleteTodo']
    props:['todos']
    
}
</script>

<style scoped>
/*main*/
  .todo-main {
    margin-left: 0px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding: 0px;
  }

  .todo-empty {
    height: 40px;
    line-height: 40px;
    border: 1px solid #ddd;
    border-radius: 2px;
    padding-left: 5px;
    margin-top: 10px;
  }
  /* vue动画 */
    .todo-enter-active{
        animation: identifier 0.5s linear;
    }
    .todo-leave-active{
        animation: identifier 0.5s reverse;
    }
    @keyframes identifier {
        from{
            transform: translateX(100%);
        }
        to{
            transform: translateX(0px);
        }
    }
</style>