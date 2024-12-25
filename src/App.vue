<!-- @format -->

<template>
	<div>
		<h2>计算属性 vs Methods 对比</h2>
		<!-- 计算属性 -->
		<div>计算属性结果: {{ fullName }}</div>

		<!-- 方法 -->
		<div>方法调用结果: {{ getFullName() }}</div>

		<!-- 触发重新渲染的按钮 -->
		<button @click="count++">点击计数: {{ count }}</button>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				firstName: '张2',
				lastName: '三',
				count: 0,
			};
		},

		computed: {
			fullName() {
				console.log('计算属性被调用');
				return this.firstName + this.lastName;
			},
		},

		methods: {
			getFullName() {
				console.log('方法被调用');
				return this.firstName + this.lastName;
			},
		},
	};
</script>
