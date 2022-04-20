<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo" @addCategory="addCategory"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" @removeTodo="removeTodo" ></TodoList>
    <TodoStatus v-bind:status="status" @changeStatus="changeStatus"></TodoStatus>
    <TodoFooter v-on:removeAll="clearAll"></TodoFooter>
    <SelectBox v-model="preselect_value" :items="somethings" :input_id="'my_selectbox'" @input="value => { preselect_value = value }"></SelectBox>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'
import SelectBox from './components/list.vue'
import TodoStatus from './components/TodoStatus.vue'


export default {
  data() {
    return {
      todoItems: [],
    }
  },
  methods: {
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
      
    },
		addTodo(todoItem) {
			localStorage.setItem(todoItem, todoItem);
			this.todoItems.push(todoItem);
		
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    

    },
    
    updateValue: function (value) {
        this.$emit('input', value);
    

    },
    
    changeStatus(index) {
      let statusIndex = this.todoStatus.indexOf(this.todoItems[index].status);

      if (++statusIndex > 2) statusIndex = 0;
      this.todoItems[index].status = this.todoStatus[statusIndex];
    }
    
   

  },
  created() {
    console.log(localStorage)
		if (localStorage.length > 0) {
			for (var i = 0; i < localStorage.length; i++) {
				this.todoItems.push(localStorage.key(i));
			}
		}
  },
  
  components: {
    'TodoHeader': TodoHeader,
    'TodoInput': TodoInput,
    'TodoList': TodoList,
    'TodoFooter': TodoFooter,
    'list': SelectBox,
    'TodoStatus': TodoStatus
  }
}
</script>

<style>
  body {
    text-align: center;
    background-color: #F6F6F8;
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03)
  }
</style>
