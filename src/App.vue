<!-- @format -->

<template>
	<div>
		<span>全选:</span>
		<input type="checkbox" />
		<button>反选</button>
		<ul>
			<li>
				<input type="checkbox" />
				<span>名字</span>
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
	};
</script>

<style></style>
