<!-- @format -->

<template>
	<div>
		<span>全选:</span>
		<input type="checkbox" v-model="bigBtn" @change="bigSelect()" />
		<button @click="invertSelection">反选</button>
		<ul>
			<li v-for="(item, index) in arr" :key="index">
				<input type="checkbox" v-model="item.c" @change="smallSelect()" />
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
				bigBtn: false,
			};
		},
		methods: {
			// 1. 小选 => 控制大选
			smallSelect() {
				// this.bigBtn = this.arr.every((item) => item.c === true);
				this.bigBtn = this.arr.every((item) => item.c === true); // 更新全选按钮状态
			},
			// 2. 大选 => 控制所有小选
			bigSelect() {
				this.arr.forEach((item) => (item.c = this.bigBtn));
			},
			// 3. 反选按钮
			invertSelection() {
				// 方法 1:
				// this.bigBtn = !this.bigBtn;
				// this.bigSelect(); // 调用方法, 更新4 个小选按钮状态
				// 方法 2:
				this.arr.forEach((item) => {
					item.c = !item.c;
				});
				this.smallSelect(); // 调用方法, 更新全选按钮状态
			},
		},
	};
</script>

<style></style>
