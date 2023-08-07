<script>
import Category from "./components/Category.vue";

export default {
  name: "App",
  components: {
    Category,
  },
  data() {
    return {
      categories: [
        { name: "HOME", color: "#8C56F6" },
        { name: "WORK", color: "#F9DC50" },
        { name: "OTHER", color: "#1E4B26" },
      ],
    };
  },
};
</script>

<template>
  <div id="app" class="app">
    <div class="my-tasks">
      <h1 class="title">My Task</h1>
      <Category v-for="category of categories" :category="category" />
    </div>
  </div>
</template>

<style>
.app {
  background: #67cb54;
  height: 100vh;
  font-family: "Dela Gothic One", Sans-serif;
}

.my-tasks {
  display: flex;
  justify-content: stretch;
  align-items: center;
  flex-direction: column;
  gap: 1rem;
}

.title {
  color: white;
  width: 100%;
  text-align: center;
}
</style>
