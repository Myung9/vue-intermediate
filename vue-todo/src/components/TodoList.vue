<template>
  <div>
      TodoList
      <ul>
        <!-- vscode상에서는 v-bind도 명시 해주어야 에러체크안남 -->
        <li v-for="todoItem in todoItems" v-bind:key="todoItem">
          {{ todoItem }}
        </li>
      </ul>
  </div>
</template>

<script>
export default {
  data: function() {
    return{
      todoItems: []
    }
  },
  created: function() {
    console.log('created');
    if(localStorage.length > 0){
      for ( var i = 0; i < localStorage.length; i++){
        if(localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoItems.push(localStorage.key(i));
          console.log(localStorage.key(i));
        }
      }
    }
  }
}
</script>

<style>

</style>