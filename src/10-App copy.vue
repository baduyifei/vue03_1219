<!-- @format -->

<template>
	<div>
		<ul>
			<li v-for="(item, i) in list" :key="i">{{ item }}</li>
		</ul>
		<h2>总分(方法调用): {{ getSum() }}</h2>
		<h2>总分(方法调用): {{ getSum() }}</h2>
		<h2>总分(方法调用): {{ getSum() }}</h2>
		<h2>总分2(计算属性): {{ getSum2 }}</h2>
		<h2>总分2(计算属性): {{ getSum2 }}</h2>
		<h2>总分2(计算属性): {{ getSum2 }}</h2>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				list: [88, 99, 100],
			};
		},
		methods: {
			getSum() {
				console.log('方法调用了');
				return this.list.reduce((sum, item) => (sum += item), 0);

				//
			},
		},
		computed: {
			getSum2() {
				console.log('计算属性调用了');
				return this.list.reduce((sum, item) => (sum += item), 0);
				//
			},
		},
	};
</script>

<style></style>
