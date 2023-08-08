<template>
  <div
  id="app"
  class="app"
  v-bind:style="[
    selectedCategory !== null
    ? { background: selectedCategory.color }
    : { background: '#67CB54' },
  ]"
  >
    <div class="my-tasks" v-if="selectedCategory">
      <h1 class="title">{{ selectedCategory.name }}</h1>
      <Tasks
      :categoryName="selectedCategory?.name"
      :data="selectedCategory?.tasks"
      :categories="categories"
      @back="() => (selectedCategory = null)"
      @updateCategories="(emitCategories) => categories = emitCategories"
      />
    </div>
    <div class="my-tasks" v-else>
      <h1 class="title">My Tasks</h1>
      <Categories
      :data="categories"
      @selectCategory="(category) => (selectedCategory = category)"
      />
    </div>
  </div>
</template>
      <script>
      import Categories from './components/Categories.vue';
      import Tasks from './components/Tasks.vue';
      import { ref } from 'vue';
      export default {
        name: 'App',
        components: {
          Categories,
          Tasks,
        },
        data() {
          return { };
        },
        setup() {
          const selectedCategory = ref(null);
          const categories = ref([
              {
                name: 'HOME',
                color: '#8C56F6',
                tasks: [
                  {
                    id: 1,
                    title: 'task 1',
                    description: 'description task 1',
                    pendingState: true,
                    timestamp: new Date()
                  },
                ],
              },
              {
                name: 'WORK',
                color: '#F9DC50',
                tasks: [
                  {
                    id: 2,
                    title: 'task 2',
                    description: 'description task 2',
                    pendingState: true,
                    timestamp: new Date()
                  },
                ],
              },
              {
                name: 'OTHER',
                color: '#1E4B26',
                tasks: [
                  {
                    id: 3,
                    title: 'task 3',
                    description: 'description task 3',
                    pendingState: true,
                    timestamp: new Date()
                  },
                  {
                    id: 4,
                    title: 'task 4',
                    description: 'description task 4',
                    pendingState: true,
                    timestamp: new Date()
                  },
                ],
              },
            ]);
          const handleCompleteTask = (task) => {
            const updatedCategories = this.categories.map((category) => {
              const updatedCategory = { ...category };
              updatedCategory.tasks = updatedCategory.tasks.map((t) => {
                if (t === task) {
                  return { ...t, pendingState: false };
                }
                return t;
              });
              return updatedCategory;
            });
            this.categories = updatedCategories;
          };
          const handleEditTask = (task) => {
            //lógica para editar una tarea aquí (formulario o modal)
          };
          const handleDeleteTask = (proxyTask, proxyCategories) => {
          };
          return {
            selectedCategory,
            categories,
            handleCompleteTask,
            handleEditTask,
            handleDeleteTask,
          };
  },
};
 </script>
<style>
.app {
  height: 100vh;
  font-family: "Inter", Sans-serif;
}
.my-tasks {
  display: flex;
  justify-content: center;
  align-content: center;
  margin:60px 700px 300px 300px;
  align-items: center;
  flex-direction: column;
  gap: 1rem;
  color: gray;
  font-family: "Inter", Sans-serif;
}
.title {
  color: white;
  width: 100%;
  text-align: center;
}
</style>









