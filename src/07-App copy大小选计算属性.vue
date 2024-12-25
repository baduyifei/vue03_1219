<!-- @format -->

<template>
	<div>
		<span>全选:</span>
		<!-- 修改这里，使用计算属性 -->
		<!-- <input type="checkbox" v-model="bigSelectBtn" @change="bigSelect" /> -->
		<input type="checkbox" v-model="isAllSelected" />
		<button @click="invertSelection">反选</button>
		<ul>
			<li v-for="(item, index) in arr" :key="index">
				<!-- <input type="checkbox" v-model="item.c" @change="smallSelect" /> -->
				<input type="checkbox" v-model="item.c" />
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
			};
		},
		methods: {
			// 1. 小选 => 控制大选
			// smallSelect() {
			// 	// this.bigSelectBtn = this.arr.every((item) => item.c === true);
			// 	this.bigSelectBtn = this.arr.every((item) => item.c === true); // 更新全选按钮状态
			// },
			// 2. 大选 => 控制所有小选
			// bigSelect() {
			// 	this.arr.forEach((item) => (item.c = this.bigSelectBtn));
			// },
			// // 3. 反选按钮
			// invertSelection() {
			// 	// 方法 1:
			// 	// this.bigSelectBtn = !this.bigSelectBtn;
			// 	// this.bigSelect(); // 调用方法, 更新4 个小选按钮状态
			// 	// 方法 2:
			// 	this.arr.forEach((item) => {
			// 		item.c = !item.c;
			// 	});
			// 	this.smallSelect(); // 调用方法, 更新全选按钮状态
			// },
			// 简化后的方法
			toggleAll() {
				this.isAllSelected = !this.isAllSelected;
			},
			invertSelection() {
				this.arr.forEach((item) => (item.c = !item.c));
			},
		},
		computed: {
			// 添加计算属性，替代原来的 bigSelectBtn
			isAllSelected: {
				get() {
					return this.arr.every((item) => item.c);
				},
				set(value) {
					this.arr.forEach((item) => (item.c = value));
				},
			},
		},
	};
</script>

<style></style>
