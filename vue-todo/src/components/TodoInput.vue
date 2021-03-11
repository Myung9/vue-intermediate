<template>
  <div>
      <!-- v-model : input에 입력된 text값을 동적으로 사용가능하게함 -->
      <input type="text" v-model="newTodoItem">
  </div>
</template>

<script>
export default {
    data: function(){
        return{
            newTodoItem: ""
        }
    }
}
</script>

<style>

</style>