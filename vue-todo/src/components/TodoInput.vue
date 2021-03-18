<template>
  <div class="inputBox shadow"> 
      <!-- v-model : input에 입력된 text값을 동적으로 사용가능하게함 -->
      <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
      <!-- <button v-on:click="addTodo">add</button> -->
      <span class="addContainer" v-on:click="addTodo">
          <i class="fas fa-plus addBtn"></i>
      </span>
  </div>
</template>

<script>
export default {
    data: function(){
        return{
            newTodoItem: ""
        } 
    },
    methods: {
        addTodo: function(){
            console.log(this.newTodoItem)
            if (this.newTodoItem !== ''){
                this.$emit('addTodoItem', this.newTodoItem);
                // localStorage.setItem(this.newTodoItem, obj)
                this.clearInput();
            }
        },
        clearInput: function(){
            this.newTodoItem = '';
        },
    }
}
</script>
<style scoped>
input:focus {
    outline: none;
}
.inputBox {
    background: white;
    height: 50px;
    line-height: 50px;
    border: 5px;
}
.inputBox input {
    border-style: none;
    font-size: 0.9rem;
}
.addContainer {
    float: right;
    background: linear-gradient(to right, #6478FB, #8763fB);
    display: block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
}
.addBtn {
    color: white;
    vertical-align: middle;
}

</style>