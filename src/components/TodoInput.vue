<template>
  <div class="inputBox shadow">
    <input type="text" v-model="newTodoItem" placeholder="할일을 입력하세요" v-on:keyup.enter="addTodo">
    <modal v-if="showModal" @close="showModal = false">
      
      <h3 slot="header">경고</h3>
      <span slot="footer" @click="showModal = false">빈칸을 모두 채워주세요.
        <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>
      </span>
    </modal>
  </div>
</template>

<script>
import Modal from './common/AlertModal.vue'

export default {
  data() {
    return {
      newTodoItem: '',
      showModal: false
    }
  },
  methods: {
    addTodo() {
      if (this.newTodoItem !== "") {
        var value = this.newTodoItem && this.newTodoItem.trim();
				this.$emit('addTodo', value)
        this.clearAddTodo();
      } else {
        this.showModal = !this.showModal;
      }
  
    },
    clearAddTodo() {
      this.newTodoItem = '';
    }
  },
  components: {
    Modal: Modal
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
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to left, #ffe7a3, #6667ab);
  display: inline-block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>
