<template>
  <section>
    <table>
        <tr class="black">
        <th id="all" type = "button" @click="all">All</th>
        <th id="mon" type = "button" @click="mon">월</th>
        <th id="tue" type = "button" @click="tue">화</th>
        <th id="wed" type = "button" @click="wed">수</th>
        <th id="thu" type = "button" @click="thu">목</th>
        <th id="fri" type = "button" @click="fri">금</th>
        <th id="sat" type = "button" @click="sat">토</th>
        <th id="sun" type = "button" @click="sun">일</th>
        
        
        </tr>
        <tr>
        <td>{{count}}</td>
        <td>{{monindex}}</td>
        <td>{{tueindex}}</td>
        <td>{{wedindex}}</td>
        <td>{{thuindex}}</td>
        <td>{{friindex}}</td>
        <td>{{satindex}}</td>
        <td>{{sunindex}}</td>
        </tr>
      </table>
    
  
    <transition-group name="list" tag="ul">


      <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
        
        <input class="final" type = "checkbox">
        
        {{ todoItem }}
        

        
        <span class="emitBtn" type="button" @click="editTodo(todoItem, index)">
          <i class="fas fa-eraser" aria-hidden="true"></i>
        </span>
        <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
          <i class="far fa-trash-alt" aria-hidden="true"></i>
        </span>
         <span class="addContainer" type = "button" @click="term" >
          <i class="fas fa-edit" aria-hidden="true"></i>
        </span>
        <span class="addContainer" type = "button" @click="modaltodo(todoItem, index)">
          <i class="fas fa-calendar" aria-hidden="true"></i>
          
        </span>
        
        <modal v-if="showModal" @close="showModal = false">

          <h3 slot="header" >기한:{{periods[indexNum]}}</h3>
          <br><h3 slot="header">세부내용:{{details[indexNum]}}</h3>
          
          
          
          
          <span slot="footer" @click="showModal = false">완료
           <i class="closeModalBtn fas fa-times" aria-hidden="true"></i>   
          </span>
      </modal>
        
        
          
        
        
      </li>
    </transition-group>
  </section>
</template>

<script>
import Modal from './common/AlertModal.vue'



export default {
  data() {
    return {
      showModal: false,
      week: 0,
      
      
      
   
     
      

    }
    
  },
  

  props: ['propsdata','count','periods','details','indexNum','monindex','tueindex','wedindex','thuindex','friindex','satindex','sunindex',],
  
  methods: {
    removeTodo(todoItem, index) {
      this.$emit('removeTodo', todoItem, index);
    },
    modaltodo(index, todoItem){
      this.showModal = !this.showModal
      this.$emit('modaltodo', todoItem, index)
      
      

    },
    term(){
        this.period = prompt("기한을 입력하시오"); 
        this.detail = prompt("세부사항을 입력하시오");
        this.$emit("addDetail",this.period,this.detail)
    },
   
    editTodo(todoItem, index){
      
      this.newItem = prompt("할 일을 수정하시오");
      this.$emit('editTodo', this.newItem, todoItem, index)
      
       },
    all(){
      document.getElementById("all").className = "black";
      document.getElementById("mon").className = "white";
      document.getElementById("tue").className = "white";
      document.getElementById("wed").className = "white";
      document.getElementById("thu").className = "white";
      document.getElementById("fri").className = "white";
      document.getElementById("sat").className = "white";
      document.getElementById("sun").className = "white";
      this.$emit('all');
    },
    mon(){
      document.getElementById("all").className = "white";
      document.getElementById("mon").className = "black";
      document.getElementById("tue").className = "white";
      document.getElementById("wed").className = "white";
      document.getElementById("thu").className = "white";
      document.getElementById("fri").className = "white";
      document.getElementById("sat").className = "white";
      document.getElementById("sun").className = "white";
      
      this.$emit('mon');

    },
    tue(){
      document.getElementById("all").className = "white";
      document.getElementById("mon").className = "white";
      document.getElementById("tue").className = "black";
      document.getElementById("wed").className = "white";
      document.getElementById("thu").className = "white";
      document.getElementById("fri").className = "white";
      document.getElementById("sat").className = "white";
      document.getElementById("sun").className = "white";
      
      this.$emit('tue');
      


    },
    wed(){
      document.getElementById("all").className = "white";
      document.getElementById("mon").className = "white";
      document.getElementById("tue").className = "white";
      document.getElementById("wed").className = "black";
      document.getElementById("thu").className = "white";
      document.getElementById("fri").className = "white";
      document.getElementById("sat").className = "white";
      document.getElementById("sun").className = "white";
      
      this.$emit('wed');
      


    },
    thu(){
      document.getElementById("all").className = "white";
      document.getElementById("mon").className = "white";
      document.getElementById("tue").className = "white";
      document.getElementById("wed").className = "white";
      document.getElementById("thu").className = "black";
      document.getElementById("fri").className = "white";
      document.getElementById("sat").className = "white";
      document.getElementById("sun").className = "white";
      
      this.$emit('thu');
      


    },

      fri(){
      document.getElementById("all").className = "white";
      document.getElementById("mon").className = "white";
      document.getElementById("tue").className = "white";
      document.getElementById("wed").className = "white";
      document.getElementById("thu").className = "white";
      document.getElementById("fri").className = "black";
      document.getElementById("sat").className = "white";
      document.getElementById("sun").className = "white";
      
      this.$emit('fri');
      


    },

      sat(){
      document.getElementById("all").className = "white";
      document.getElementById("mon").className = "white";
      document.getElementById("tue").className = "white";
      document.getElementById("wed").className = "white";
      document.getElementById("thu").className = "white";
      document.getElementById("fri").className = "white";
      document.getElementById("sat").className = "black";
      document.getElementById("sun").className = "white";
      
      this.$emit('sat');
      


    },

      sun(){
      document.getElementById("all").className = "white";
      document.getElementById("mon").className = "white";
      document.getElementById("tue").className = "white";
      document.getElementById("wed").className = "white";
      document.getElementById("thu").className = "white";
      document.getElementById("fri").className = "white";
      document.getElementById("sat").className = "white";
      document.getElementById("sun").className = "black";
      
      this.$emit('sun');
      


    },




    
    
    
    
    
    
   
   
  },
    
  
    

   components: {
    Modal: Modal
  } 
}


</script>

<style scoped>
  ul {
    list-style-type: none;
    padding-left: 0px;
    margin-top: 0;
    text-align: left;
  }
  li {
    display: flex;
    min-height: 50px;
    height: 50px;
    line-height: 50px;
    margin: 0.5rem 0;
    padding: 0 0.9rem;
    background: white;
    border-radius: 5px;
  }
  .checkBtn {
    line-height: 45px;
    color: #62acde;
    margin-right: 5px;
  }
  .removeBtn {
    margin-left: auto;
    margin-right: 5px;
    color: #de4343;
  }

  .list-enter-active, .list-leave-active {
    transition: all 1s;
  }
  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
  .addContainer {
  float: right;
  
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: inline-block;
  width: 3rem;
  border-radius: 5px 5px 5px 5px;
  text-align: center;
  }

  .addBtn {
  color: white;
  vertical-align: middle;
  
  }
  .form-text {
  box-sizing: border-box;
  width: 100%;
  height: 32px;
  margin: 0 auto;
}
.final{
  float: left;
  width: 2rem;  
  vertical-align: middle;
}
table {
    width: 100%;
    border-collapse: separate;
    border-spacing: 1px;
    text-align: center;
    line-height: 1.5;
    
  }
  th {
    font-weight: bold;
    vertical-align: top;
    color: #fff;
    background: #ce4869;
    border-radius: 5px 5px / 5px 5px;
  }
  td {
    vertical-align: top;
    border-bottom: 1px solid #ccc;
    background: #eee;
    border-radius: 5px 5px / 5px 5px;
  }
  .emitBtn{
    margin: 5px;
  }
.black{
  color: black;
}
.white{
  color: white;
}

  
</style>
