<template>

  <form class="new-task" @submit.prevent="addTask">
    <input v-model="newTaskTitle" placeholder="Enter task title" />
    <textarea v-model="newTaskDescription" placeholder="Enter task description"></textarea>
    <button class="Add" type="submit">Add Task</button>
  </form>
  <div class="task-wrapper">
    <div class="task-band"></div>
    <input type="checkbox" v-model="toggle" true-value="yes" false-value="no" />
    <div class="task-body">
      <span id="title">{{ data?.title }}</span>
      <span>{{ data?.description }}</span>
    </div>
   <button @click="editTask">Edit</button>
   <button @click="deleteTask">Delete</button>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    categoryName: String,
    data: Object,
  },
  methods: {
    completeTask() {
      this.$emit('completeTask', { ...this.data, categoryName: this.categoryName });
    },
    editTask() {
      this.$emit('editTask', { ...this.data, categoryName: this.categoryName });
    },
    deleteTask() {
      this.$emit('deleteTask', { ...this.data, categoryName: this.categoryName });
    },
  },
};

</script>
<style>
.task-wrapper {
  width: 500px;
  height: 60px;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 5px;
  background: transparent;
  border:solid;
  border-width: 1px;
  border-color: #ffffff;
  padding-right: 15px;
  margin-top: 20px;
}
#title{
  text-transform:capitalize;
  font-size: larger;

}
/* .task-band {
  width: 10%;
  height: 100%;
  background-color: '#949AA8';
} */
button {
  box-shadow: 0px 10px 14px -7px #3E7327;
  background:linear-gradient(to bottom, #77B55A 5%, #72B352 100%);
  background-color:#77b55a;
  border-radius:4px;
  border:1px solid #4B8F29;
  display:inline-block;
  cursor:pointer;
  color:#ffffff;
  font-family:sans-serif;
  font-size:13px;
  font-weight:bold;
  padding:6px 12px;
  text-decoration:none;
  text-shadow:0px 1px 0px #5B8A3C;
}
#Completed {
  margin-right: 20px;
  margin-left:0px;

}

textarea{
margin-left:20px;
}
 .new-task{
  margin-top: 30px;
  display: flex;
  justify-content: center;
}
.Add {
  margin-left: 20px;
}
input{
  border-radius: 15px;
  border-block-color:inherit;
}
.task-body {
  display:contents;
  justify-content: space-between;
  align-items: flex-start;
  flex-direction: column;
  width: 80%;
  font-family: "Inter", Sans-serif;
  color:#ffffff;
  font-size: medium;
}
</style>






