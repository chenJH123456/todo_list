//JS
<script setup>
	import { reactive, ref } from 'vue'
	const thingsList = reactive([])
	const scanf = ref('')
	const dataEl = ref('')

	const add = () => {
		thingsList.push({
			content: scanf.value,
			time: dataEl.value,
		})
		scanf.value = ''
	}

	const deleteitem = (index) => {
		thingsList.splice(index, 1)
	}
</script>

//HTML
<template>
	<div class="wrapper">
		<div class="title">
			<input
				type="text"
				v-model="scanf"
				class="inputstyle"
				placeholder="...添加待办任务" />
			<div class="text">截止日期</div>
			<input v-model="dataEl" type="date" />
			<button @click="add" class="addstyle">添加</button>
			<button @click="sort" class="sortstyle">按截止日期排序</button>
		</div>

		<template v-for="(item, index) in thingsList" :key="(item, time)">
			<div class="list">
				<div class="list-left">
					<div class="text">{{ item.content }}</div>
					<div class="endless">截至日期:{{ item.time }}</div>
				</div>
				<div class="list-right">
					<button @click="deleteitem(index)" class="deleteItem">删除</button>
				</div>
			</div>
		</template>
	</div>
</template>

//CSS
<style scoped>
	.wrapper .title {
		margin-top: 50px;
		/* background-color: red; */
	}
	.wrapper .title .text {
		display: inline-block;
		margin-right: 3px;
		height: 40px;
		line-height: 40px;
		font-size: 12px;
		/* background-color: yellow; */
	}
	.wrapper .title .inputstyle {
		width: 400px;
		height: 40px;
		line-height: 40px;
		margin: 10px;
		font-size: 16px;
	}
	.wrapper .title .addstyle {
		width: 70px;
		height: 40px;
		margin: 5px;
		font-size: 14px;
	}
	.wrapper .title .sortstyle {
		height: 40px;
		margin-right: 10px;
		font-size: 14px;
	}
	.list {
		display: flex;
		width: 800px;
		height: 200px;
		margin-top: 45px;
		border-radius: 7px;
		-webkit-box-shadow: #fff 0 -1px 4px, #ff0 0 -2px 10px, #ff8000 0 -10px 20px,
			rgb(25, 0, 255) 0 -18px 40px, 5px 5px 15px 5px rgba(0, 0, 0, 0);
		box-shadow: #fff 0 -1px 4px, #ff0 0 -2px 10px, #ff8000 0 -10px 20px,
			rgba(255, 38, 0, 0.39) 0 -18px 40px, 5px 5px 15px 5px rgba(0, 0, 0, 0);
		background: #fafbf0;
	}
	.list .list-left {
		display: flex;
		/* justify-content: center; */
		width: 600px;
		height: 200px;
		margin: 0 auto;
	}
	.list .list-left .text {
		margin: auto;
		font-size: 20px;
		font-weight: 600;
	}
	.list .list-left .endless {
		margin-left: auto;
	}
	.list .list-right {
		display: flex;
		/* justify-content: center; */
		width: 200px;
		height: 200px;
	}
	.list .list-right .deleteItem {
		width: 100px;
		height: 50px;
		margin: auto;
		/* align-items: center; */
	}
</style>
