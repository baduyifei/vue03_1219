<!-- @format -->

<template>
	<div>
		<span>全选:</span>
		<input type="checkbox" v-model="bigSelectBtn" />
		<!-- <button>反选</button> -->
		<ul>
			<li v-for="(item, index) in arr" :key="index">
				<input type="checkbox" v-model="item.c" @click="smallSelect" />
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
				bigSelectBtn: false,
			};
		},
		methods: {
			smallSelect() {
				// this.bigSelectBtn = this.arr.every((item) => item.c === true);
				this.bigSelectBtn = this.arr.every((item) => item.c); // 更新全选按钮状态
			},
		},
	};
</script>

<style></style>
