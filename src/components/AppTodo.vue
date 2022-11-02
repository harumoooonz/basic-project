<template>
   <div class="todo-item" v-bind:class="{'is-complete':item.completed}">
      <p>
        <input type="checkbox" 
               v-on:change="markComplete">
        {{item.name}}
        <button class="deletebutton"
                v-on:click="$emit('del-todo',item)"> 削除 </button>
      </p>
   </div>
</template>


<script>
  export default {
    name: 'AppTodo',
    props:["item"],
    methods:{
       markComplete() {
        console.log(123);
        this.$emit("check-mark", this.item);
       } 
    }
  }

</script>


<style scoped>
 .todo-item{
  padding: 10px;
  border-bottom:1px #ccc dotted;
 }
 
 .is-complete{
  background-color: bisque;
 }

</style>
