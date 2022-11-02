<template>
  <div>
    Todoを入力：
    <input 
      v-model="message"
      type="text" placeholder="入力してください">
    <input
      type="submit" value="追加"   
      v-on:click="createItem">

</div>
</template>

<script>
export default {
  name:"AddTodo",
  data(){
    return{
      message:''
    }
  },
  methods:{
    createItem(){
      const getRandomId = Math.floor(Math.random()*(10000-1)+1);
      console.log(getRandomId);
      const newItem = {
        id:getRandomId,
        name:this.message,
        completed:false
      };
      // console.log(newItem)

    this.$emit('add-todo',newItem)
    }
  }

// 

// 追加ボタンを押す
// 配列に入力内容が送られる
// 配列の最後に追加される, array.push(入力されたmessage)
}
</script>

<style scoped>

</style>
