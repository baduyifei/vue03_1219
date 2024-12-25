<!-- @format -->

<template>
	<div>
		<ul>
			<li v-for="(item, i) in list" :key="i">{{ item }}</li>
		</ul>
		<h2>{{ getSum() }}</h2>
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
				return this.list.reduce((sum, item) => (sum += item), 0);
				//
			},
		},
	};
</script>

<style></style>
