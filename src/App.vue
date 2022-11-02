<template>
  <div>
    <AppTitle />
    <AddTodo v-on:add-todo="addTodoButton"/>
    <AppTodoList
      v-on:check-mark-p="checkedBoxParent"
      v-bind:list="todolist" 
      v-on:del-todo="deleteTodo"
    />

  </div>
</template>


<script>
import AppTitle from './components/AppTitle.vue';
import AddTodo from './components/AddTodo.vue';
import AppTodoList from './components/AppTodoList.vue';

export default {
  name: 'App',
  components: {
    AppTitle,
    AddTodo,
    AppTodoList,
  },
  data(){
    return{
      todolist:[
        {
          id:1,
          name:"いぬ",
          completed:false
        },
         {
          id:2,
          name:"ねこ",
          completed:false
        },
         {
          id:3,
          name:"とり",
          completed:false
        },
      ]
    }
  },
  methods:{
    // リストを消したい
    deleteTodo(item){
      // 配列で、選ばれたelement以外の配列を返して表示する
      this.todolist = this.todolist.filter(e => e.id !== item.id);
    },

    // チェックボックスで色をつけたい
    checkedBoxParent(item){
      // 配列の要素を取得
      const getitem = this.todolist.find(e => e.id === item.id);
      // completedを変更する
      getitem.completed = !getitem.completed;
      // 配列を作り直す
    },
    
    // 追加ボタンの発火
    addTodoButton(newItem){
      console.log(newItem);
      //  これはダメらしい↓
      //  this.todolist = this.todolist.(newItem); 
      this.todolist = [ ...this.todolist,newItem];
      
    }
  }
}
</script>

<style>


</style>
