<!-- @format -->

<template>
	<div>
		<span>全选:</span>
		<input type="checkbox" v-model="selectAll" @change="bigCheckSelectAll" />
		<!-- <button @click="handleInvert">反选</button> -->
		<ul>
			<li v-for="(item, index) in arr" :key="index">
				<input type="checkbox" v-model="item.c" @change="smallCK" />
				<span>{{ item.name }}</span>
			</li>
		</ul>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				arr: [
					{
						name: '猪八戒',
						c: false,
					},
					{
						name: '孙悟空',
						c: false,
					},
					{
						name: '唐僧',
						c: false,
					},
					{
						name: '白龙马',
						c: false,
					},
				],
				selectAll: false,
			};
		},
		methods: {
			// // 小选按钮:
			// smallCheckSelectAll() {
			// 	let num = 0;
			// 	this.arr.forEach((item) => {
			// 		if (item.c === true) {
			// 			num++;
			// 		}
			// 	});
			// 	if (num === this.arr.length) {
			// 		this.selectAll = true;
			// 	} else {
			// 		this.selectAll = false;
			// 	}
			// 	//
			// },
			smallCK() {
				this.selectAll = this.arr.every((item) => item.c === true);
			},
			// 大选按钮: 添加全选处理方法
			bigCheckSelectAll() {
				this.arr.forEach((item) => {
					item.c = this.selectAll;
				});
			},

			// // 添加反选方法
			// handleInvert() {
			// 	this.arr.forEach((item) => {
			// 		item.c = !item.c;
			// 	});
			// 	this.checkSelectAll(); // 反选后检查全选状态
			// },
			//
		},
	};
</script>

<style></style>
