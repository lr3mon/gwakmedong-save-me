<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems" v-bind:count="count" v-bind:periods="periods" v-bind:details="details" v-bind:indexNum="indexNum"
    @removeTodo="removeTodo" v-on:editTodo="editTodo" v-on:addDetail="addDetail" v-on:modaltodo="modaltodo" v-on:mon="mon"
    v-on:tue="tue" v-on:all="all" v-on:wed="wed" v-on:thu="thu" v-on:fri="fri" v-on:sat="sat" v-on:sun="sun" v-bind:monindex="monindex"
    v-bind:tueindex="tueindex" v-bind:wedindex="wedindex" v-bind:thuindex="thuindex" v-bind:friindex="friindex" v-bind:satindex="satindex"
    v-bind:sunindex="sunindex"></TodoList>
    <TodoFooter v-on:removeAll="clearAll" ></TodoFooter>
    <!-- <AlterModal v-on:playModal ="executeModal"></AlterModal> -->
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'
// import AlterModal from '/components/common/AlertModal.vue'

export default {
  data() {
    

    
    return {
      todoItems: [],
      count: 0,
      periods: [],
      details: [],
      indexNum: 0,
      original: [],
      alllist:[],
      monlist: [],
      monindex: 0,
      tueindex: 0,
      wedindex: 0,
      thuindex: 0,
      friindex: 0,
      satindex: 0,
      sunindex: 0,
      tuelist: [],
      wedlist: [],
      thulist: [],
      frilist: [],
      satlist: [],
      sunlist: [],
      
      
      

    }
  },
  methods: {
    
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
      this.count=0;
      this.periods= [];
      this.details = [];
      this.alllist = [];      
      this.original = [];
      this.monlist = [];
      this.tuelist = [];
      this.wedlist = [];
      this.thulist = [];
      this.frilist = [];
      this.satlist = [];
      this.sunlist = [];
      this.monindex = 0;
      this.tueindex = 0;
      this.wedindex = 0;
      this.thuindex = 0;
      this.friindex = 0;
      this.satindex = 0;
      this.sunindex = 0;

    },
		addTodo(todoItem) {
			localStorage.setItem(todoItem, todoItem);
      

			this.todoItems.push(todoItem);
      this.count++;
      this.monindex = this.monlist.length
      this.tueindex = this.tuelist.length
      this.wedindex = this.wedlist.length
      this.thuindex = this.thulist.length
      this.friindex = this.frilist.length
      this.satindex = this.satlist.length
      this.sunindex = this.sunlist.length

      
		},
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
      this.periods.splice(index, 1);
      this.details.splice(index, 1);
      this.count--;
    },
    editTodo(newItem, todoItem, index){
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1)
      this.todoItems.splice(index, 0, newItem);
      

    },
    addDetail(period, detail){
      localStorage.setItem(period, period);
      localStorage.setItem(detail, detail);
      this.periods.push(period);
      this.details.push(detail);

    },
    modaltodo(index){
      this.indexNum = index;
    },
    
    all(){
      this.todoItems = this.original;
      this.original = this.todoItems;
      this.todoItems = this.todoItems.concat(this.alllist);
      this.todoItems = this.todoItems.concat(this.monlist);
      this.todoItems = this.todoItems.concat(this.tuelist);
      this.todoItems = this.todoItems.concat(this.wedlist);
      this.todoItems = this.todoItems.concat(this.thulist);
      this.todoItems = this.todoItems.concat(this.frilist);
      this.todoItems = this.todoItems.concat(this.satlist);
      this.todoItems = this.todoItems.concat(this.sunlist);

     
      
    },
    
    

    
    mon(){
      
      this.todoItems = this.original;
      this.original = this.todoItems;
      this.todoItems = this.monlist;
    },
    tue(){
      
      this.todoItems = this.original;
      this.original = this.todoItems;
      this.todoItems = this.tuelist;
    },
     wed(){
      
      this.todoItems = this.original;
      this.original = this.todoItems;
      this.todoItems = this.wedlist;
    },
     thu(){
      
      this.todoItems = this.original;
      this.original = this.todoItems;
      this.todoItems = this.thulist;
    },
    fri(){
      
      this.todoItems = this.original;
      this.original = this.todoItems;
      this.todoItems = this.frilist;
    },
    sat(){
      
      this.todoItems = this.original;
      this.original = this.todoItems;
      this.todoItems = this.satlist;
    },
    sun(){
      
      this.todoItems = this.original;
      this.original = this.todoItems;
      this.todoItems = this.sunlist;
    },
   

    
      
    
    
    
  
    
    
   
   
    
    
    

    
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
