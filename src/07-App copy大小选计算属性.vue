<!-- @format -->

<template>
	<div>
		<span>全选:</span>
		<input type="checkbox" v-model="isAllSelected" />
		<button @click="invertSelection">反选</button>
		<ul>
			<li v-for="(item, index) in arr" :key="index">
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
			invertSelection() {
				this.arr.forEach((item) => (item.c = !item.c));
			},
		},
		computed: {
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
