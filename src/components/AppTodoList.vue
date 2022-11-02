<template>
   <div class="todo-list">
      <p v-for="(item,index) in list" v-bind:key=index>
        <AppTodo 
          v-on:check-mark="chedkedBox"
          v-bind:item="item" 
          v-on:del-todo="$emit('del-todo',item)"
          />
      </p>
   </div> 

   <!-- v-on:checkbox-mark="$emit('checkbox-mark','item')" -->

</template>


<script>
  import AppTodo from "./AppTodo.vue";

  export default {
    name: 'AppTodoList',
    components:{
      AppTodo
    },
    props:["list"],
    methods:{
      chedkedBox(item){
        this.$emit('check-mark-p',item)
      }
    }
  }
</script>


<style scoped>
 .todo-list p{
  margin: 0px;
 }
</style>
