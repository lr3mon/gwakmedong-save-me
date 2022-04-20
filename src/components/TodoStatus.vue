<template>
    <div>
        <div class="status-indicator"
            :class="{
                'status-indicator-todo': todoItem.status === 'todo',
                'status-indicator-ongoing': todoItem.status === 'on-going',
                'status-indicator-finished': todoItem.status === 'finished',
            }"
        ></div>
        <div class="status-text" @click="changeStatus(index)"
            :class="{
                'status-text-todo': todoItem.status === 'to=do',
                'status-text-ongoing': todoItem.status === 'on-going',
                'status-text-finished': todoItem.status === 'finished',
            }"
        ></div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            todoStatus: ["to-do", "on-going", "finished"]
        }
    },
    methods: {
        changeStatus(index) {
            let statusIndex = this.todoStatus.indexOf(this.todoItems[index].status);

            if (++ statusIndex > 2) statusIndex = 0;
            this.todoItems[index].status = this.todoStatus[statusIndex];
        }
    }
}

methods
</script>




<style> scoped>
.todo-finished {
  font-style: italic;
  text-decoration: line-through;
}
.status-indicator {
  width: 10px;
  height: 10px;
  border-radius: 50%;
}
.status-indicator-todo {
  background: red;
}
.status-indicator-ongoing {
  background: yellow;
}
.status-indicator-finished {
  background: green;
}
.status-text {
  font-weight: bold;
  cursor: pointer;
}
.status-text-todo {
  color: red;
}
.status-text-ongoing {
  color: yellow;
}
.status-text-finished {
  color: green;
}
</style>