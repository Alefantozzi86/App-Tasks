<template>
  <div>
    <button id="my-button" @click="$emit('back')">Back</button>
    <div class="new-task">
      <input v-model="title" placeholder="Enter task title" />
      <textarea v-model="description" placeholder="Enter task description"></textarea>
      <button class="Add" @click="() => { addTask(title, description, categoryName, categories); title = ''; description = ''}">Add Task</button>
    </div>
    <Task
      v-for="task of data"
      :data="task"
      :key="task.id"
      :categoryName="categoryName"
      @completeTask="(emitObject) => changePendingState(emitObject, categories, false)"
      @unCompleteTask="(emitObject) => changePendingState(emitObject, categories, true)"
      @editTask="(emitObject) =>  editTask(emitObject)"
      @deleteTask="(emitObject) => deleteTask(emitObject, categories)"
      @addTask="handleAddTask"
      />
    </div>
  </template>
<script>
import Task from "./Task.vue";
import { toRaw, ref } from 'vue';
export default {
  name: "Tasks",
  props: {
    categoryName: String,
    data: Object,
    categories: Object
  },
  components: {
    Task,
  },
  emits: ['back', 'editTask', 'updateCategories'],
  methods: {
    back() {
      this.$emit('back');
    },
    addTask(proxyTitle, proxyDescription, proxyCategoryName, proxyCategories) {
      const rawCategories = toRaw(proxyCategories);
      const categoryName = toRaw(proxyCategoryName);
      const description = toRaw(proxyDescription);
      const title = toRaw(proxyTitle);
      const [ category ] = rawCategories.filter(i => i.name === categoryName);
      const now = new Date()
      category.tasks.push({ id: now.toISOString() , title, description, pendingState: true, timestamp: now })
      const categories = rawCategories.map(i => {
        if(i.name === categoryName) {
          return category;
        } else {
          return i;
        }
      })
      this.$emit('updateCategories', categories);
    },
    editTask(task) {
      this.$emit('editTask', task);
    },
    changePendingState(proxyTask, proxyCategories, proxyPendingState) {
      const task = toRaw(proxyTask);
      const rawCategories = toRaw(proxyCategories);
      const pendingState = toRaw(proxyPendingState);
      const updatedCategories = rawCategories.map((category) => {
        if(category.name === task.categoryName) {
          const tasks = category.tasks.map(i => {
            if(i.id == task.id) {
              return { ...task, pendingState }
            } else {
              return i
            }
          });
          category.tasks = tasks;
          return category;
        } else {
          return category;
        }
      })
      this.$emit('updateCategories', updatedCategories);
    },
    deleteTask(proxyTask, proxyCategories) {
      const task = toRaw(proxyTask);
      const rawCategories = toRaw(proxyCategories);
      const updatedCategories = rawCategories.map((category) => {
        if(category.name === task.categoryName) {
          const tasks = category.tasks.filter(categoryTask => categoryTask.id !== task.id);
          category.tasks = tasks;
          return category;
        } else {
          return category;
        }
      })
      this.$emit('updateCategories', updatedCategories);
    },
  },
  data() {
    return {
      title: ref(''),
      description: ref('')
    }
  },
};
</script>
<script setup>
defineProps(["data", "categoryName", "categories"]);
defineEmits(["back"]);
</script>
<style>
#my-button {
  padding: 12px 15px;
}
</style>










