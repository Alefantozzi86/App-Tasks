<template>
  <div class="category-wrapper">
    <div
      class="category-band"
      :style="{ 'background-color': category.color }"
    ></div>
    <span class="category-name">{{ category.name }}</span>
   <button> Edit</button>
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
  justify-content:space-between;
  margin-top:8px;
  margin-bottom: 15px;
  border-radius: 8px;
  align-items: center;
  gap: 5px;
  background: #eff2ef;
  padding-right: 10px;
}


.category-band {
  width: 10%;
  height: 100%;
  border-top-left-radius: 8px;
  border-bottom-left-radius: 8px;
}

.category-name {
  width: 80%;
  font-size:larger;
  margin-left: 10px;
}
</style>
