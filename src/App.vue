<!-- @format -->

<template>
	<div class="score-case">
		<div class="table">
			<table>
				<thead>
					<tr>
						<th>编号</th>
						<th>科目</th>
						<th>成绩</th>
						<th>考试时间</th>
						<th>操作</th>
					</tr>
				</thead>
				<tbody v-if="list.length !== 0">
					<tr v-for="(item, index) in list" :key="item.id">
						<td>{{ index + 1 }}</td>
						<td>{{ item.subject }}</td>
						<td class="red">{{ item.score }}</td>
						<td>{{ timeFormat(item.date) }}</td>
						<td><a href="#" @click="deleteData(item.id)">删除</a></td>
					</tr>
				</tbody>
				<tbody v-else>
					<tr>
						<td colspan="5">
							<span class="none">暂无数据</span>
						</td>
					</tr>
				</tbody>
				<tbody>
					<button @click="edit()">点击修改分数</button>
				</tbody>
				<tfoot>
					<tr>
						<td colspan="5">
							<span>总分：{{ getSum }}</span>
							<span style="margin-left: 50px">平均分：{{ getAverage }}</span>
						</td>
					</tr>
				</tfoot>
			</table>
		</div>
		<div class="form">
			<div class="form-item">
				<div class="label">科目：</div>
				<div class="input">
					<input type="text" placeholder="请输入科目" v-model="subject" />
				</div>
			</div>
			<div class="form-item">
				<div class="label">分数：</div>
				<div class="input">
					<input type="text" placeholder="请输入分数" v-model="score" />
				</div>
			</div>
			<div class="form-item">
				<div class="label"></div>
				<div class="input">
					<button class="submit" @click="add">添加</button>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
	import moment from 'moment';

	export default {
		name: 'ScoreCase',
		data() {
			return {
				// list: [
				// 	{id: 15, subject: '语文', score: 89, date: new Date('2022/06/07 10:00:00')},
				// 	{id: 27, subject: '数学', score: 100, date: new Date('2022/06/07 15:00:00')},
				// 	{id: 32, subject: '英语', score: 56, date: new Date('2022/06/08 10:00:00')},
				// 	{id: 41, subject: '物理', score: 76, date: new Date('2022/06/08 10:00:00')},
				// ],
				list: JSON.parse(localStorage.getItem('dataKey')) || [],
				subject: '',
				score: '',
			};
		},

		methods: {
			add() {
				if (this.subject === '' || this.score === '') {
					return alert('输入不能为空');
				}
				const obj = {
					id: Math.random(),
					subject: this.subject,
					score: +this.score,
					date: new Date(),
				};
				this.list.push(obj);
				this.subject = '';
				this.score = '';
				// // ls 本地化
				// localStorage.setItem('dataKey', JSON.stringify(this.list));
			},
			deleteData(id) {
				// this.list.splice(id, 1);
				// 使用 findIndex 找到正确的数组索引
				const index = this.list.findIndex((item) => item.id === id);
				if (index !== -1) {
					this.list.splice(index, 1);
				}
				// // ls 本地化
				// localStorage.setItem('dataKey', JSON.stringify(this.list));
			},
			timeFormat(timeStr) {
				return moment(timeStr).format('YYYY-MM-DD HH:mm:ss');
			},
			edit() {
				this.list[0].score = +Math.floor(Math.random() * 100);
			},
		},
		computed: {
			getSum() {
				return this.list.reduce((sum, item) => (sum += item.score), 0);
			},
			getAverage() {
				return this.list.length ? (this.getSum / this.list.length).toFixed(2) : 0;
			},
		},
		watch: {
			// 简单写法
			// list() {
			// 	// ls 本地化
			// 	localStorage.setItem('dataKey', JSON.stringify(this.list));
			// },
			// 完整写法
			list: {
				deep: true,
				handler() {
					localStorage.setItem('dataKey', JSON.stringify(this.list));
				},
			},
		},
	};
</script>

<style lang="less">
	.score-case {
		width: 1000px;
		margin: 50px auto;
		display: flex;
		.table {
			flex: 4;
			table {
				width: 100%;
				border-spacing: 0;
				border-top: 1px solid #ccc;
				border-left: 1px solid #ccc;
				th {
					background: #f5f5f5;
				}
				tr:hover td {
					background: #f5f5f5;
				}
				td,
				th {
					border-bottom: 1px solid #ccc;
					border-right: 1px solid #ccc;
					text-align: center;
					padding: 10px;
					&.red {
						color: red;
					}
				}
			}
			.none {
				height: 100px;
				line-height: 100px;
				color: #999;
			}
		}
		.form {
			flex: 1;
			padding: 20px;
			.form-item {
				display: flex;
				margin-bottom: 20px;
				align-items: center;
			}
			.form-item .label {
				width: 60px;
				text-align: right;
				font-size: 14px;
			}
			.form-item .input {
				flex: 1;
			}
			.form-item input,
			.form-item select {
				appearance: none;
				outline: none;
				border: 1px solid #ccc;
				width: 200px;
				height: 40px;
				box-sizing: border-box;
				padding: 10px;
				color: #666;
			}
			.form-item input::placeholder {
				color: #666;
			}
			.form-item .cancel,
			.form-item .submit {
				appearance: none;
				outline: none;
				border: 1px solid #ccc;
				border-radius: 4px;
				padding: 4px 10px;
				margin-right: 10px;
				font-size: 12px;
				background: #ccc;
			}
			.form-item .submit {
				border-color: #069;
				background: #069;
				color: #fff;
			}
		}
	}
</style>
