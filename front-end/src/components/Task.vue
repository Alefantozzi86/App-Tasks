<template>
  <div class="task-wrapper">
    <div class="task-band"></div>
    <div class="task-body">
      <span>{{ data?.title }}</span>
      <span>{{ data?.description }}</span>
    </div>
    <span>0</span>
    <span>📝</span>
    <span>X</span>
  </div>
</template>

<script>
export default {
  name: 'Task',
  props: {
    data: Object,
  },
};
</script>

<style>
.task-wrapper {
  width: 300px;
  height: 50px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 5px;
  background: #eff2ef;
  padding-right: 5px;
}

.task-band {
  width: 10%;
  height: 100%;
  background-color: '#949AA8';
}

.task-body {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-direction: column;
  width: 80%;
}
</style>
