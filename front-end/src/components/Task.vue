<template>
  <div class="task-wrapper">
    <div class="task-band"></div>
    <div class="task-body">
      <span>{{ data?.title }}</span>
      <span>{{ data?.description }}</span>
    </div>
   <button>Completed</button>
   <button>Edit</button>
   <button>Delete</button>
   
  
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
  width: 500px;
  height: 60px;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  gap: 5px;
  background:#eff2ef;
  padding-right: 15px;
  margin-top: 20px;
}

.task-band {
  width: 10%;
  height: 100%;
  background-color: '#949AA8';
}

button {
  box-shadow: 0px 10px 14px -7px #3e7327;
	background:linear-gradient(to bottom, #77b55a 5%, #72b352 100%);
	background-color:#77b55a;
	border-radius:4px;
	border:1px solid #4b8f29;
	display:inline-block;
	cursor:pointer;
	color:#ffffff;
	font-family:sans-serif;
	font-size:13px;
	font-weight:bold;
	padding:6px 12px;
	text-decoration:none;
	text-shadow:0px 1px 0px #5b8a3c;
}
.task-body {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-direction: column;
  width: 80%;
}
</style>
