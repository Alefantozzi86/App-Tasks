<template>
  <div class="category-wrapper">
    <div
      class="category-band"
      :style="{ 'background-color': category.color }"
    ></div>
    <span class="category-name">{{ category.name }}</span>
    <span>📝</span>
  </div>
</template>

<script>
export default {
  name: 'Category',
  props: {
    category: Object,
  },
};
</script>

<style>
.category-wrapper {
  width: 300px;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 5px;
  background: #eff2ef;
  padding-right: 5px;
}

.category-band {
  width: 10%;
  height: 100%;
}

.category-name {
  width: 80%;
}
</style>
