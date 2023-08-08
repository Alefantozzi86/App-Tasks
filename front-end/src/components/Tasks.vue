<template>
  <div>
    <button id="my-button" @click="$emit('back')">Back</button>
    <Task
      v-for="task of data"
      :data="task"
      :key="task.id"
      @completeTask="completeTask(task)"
      @editTask="editTask(task)"
      @deleteTask="deleteTask(task)"
    />
  </div>
</template>

<script>
import Task from "./Task.vue";

export default {
  name: "Tasks",
  props: {
    data: Object,
  },
  components: {
    Task,
  },
  emits: ['back', 'completeTask', 'editTask', 'deleteTask'],
  methods: {
    back() {
      this.$emit('back');
    },
    completeTask(task) {
      this.$emit('completeTask', task);
    },
    editTask(task) {
      this.$emit('editTask', task);
    },
    deleteTask(task) {
      this.$emit('deleteTask', task);
    },
  },

};
</script>

<script setup>
defineProps(["data"]);
defineEmits(["back"]);
</script>

<style>
#my-button {
  padding: 12px 15px;
}
</style>
