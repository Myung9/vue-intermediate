<template>
  <div class="inputBox shadow"> 
      <!-- v-model : input에 입력된 text값을 동적으로 사용가능하게함 -->
      <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
      <!-- <button v-on:click="addTodo">add</button> -->
      <span class="addContainer" v-on:click="addTodo">
          <i class="fas fa-plus addBtn"></i>
      </span>
      
    <!-- use the modal component, pass in the prop -->
    <Modal v-if="showModal" @close="showModal = false">
            <!--
            you can use custom content here to overwrite
            default content
            -->

        <h3 slot="header">
            경고!
            <i class="closeModalBtn fas fa-times" @click="showModal = false"></i>
        </h3>
        <!-- 
        body : input something
        footer : copy right
         -->
        <div slot="body">
            input somthing
        </div>
        <div slot="footer">
            copyright
        </div>
    </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue'


export default {
    data: function(){
        return{
            newTodoItem: "",
            showModal: false
        } 
    },
    methods: {
        addTodo: function(){
            console.log(this.newTodoItem)
            if (this.newTodoItem !== ''){
                this.$emit('addTodoItem', this.newTodoItem);
                // localStorage.setItem(this.newTodoItem, obj)
                this.clearInput();
            } else {
                // alert();
                this.showModal = !this.showModal;
            }
        },
        clearInput: function(){
            this.newTodoItem = '';
        },
    },
    components: {
        Modal: Modal
    },
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
.closeModalBtn {
    color: #42b983;
}
</style>