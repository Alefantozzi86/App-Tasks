<template>
  <div
  id="app"
  class="app"
  v-bind:style="[
    selectedCategory !== null
    ? { background: selectedCategory.color }
    : { background: '#67cb54' },
  ]"
  >
    <div class="my-tasks" v-if="selectedCategory">
      <h1 class="title">{{ selectedCategory.name }}</h1>
      <Tasks
      :data="selectedCategory?.tasks"
      @back="() => (selectedCategory = null)"
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
          return {
            categories: [
              {
                name: 'HOME',
                color: '#8C56F6',
                tasks: [
                  {
                    title: 'task 1',
                    description: 'description task 1',
                    pendingState: true,
                  },
                ],
              },
              {
                name: 'WORK',
                color: '#F9DC50',
                tasks: [
                  {
                    title: 'task 2',
                    description: 'description task 2',
                    pendingState: true,
                  },
                ],
              },
              {
                name: 'OTHER',
                color: '#1E4B26',
                tasks: [
                  {
                    title: 'task 3',
                    description: 'description task 3',
                    pendingState: true,
                  },
                ],
              },
            ],
          };
        },
        setup() {
          const selectedCategory = ref(null);
          return {
            selectedCategory,
          };
        },
      };
      </script>
<style>
.app {
  height: 100vh;
  font-family: 'Dela Gothic One', Sans-serif;
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
