<template>
	<section class="data_section" ref="data_section">

		<el-row :gutter="10" class="row_list order_list">
			<el-col :span="7">
				<log-list></log-list>
			</el-col>
			<el-col :span="17">
				<bar-chart type="barChart"></bar-chart>
			</el-col>
		</el-row>
		<el-row :gutter="10" class="row_list order_list ">
			<el-col :span="7">
				<sales-table></sales-table>
			</el-col>
			<el-col :span="10" class="wrapper">
				<card-list></card-list>

			</el-col>
			<el-col :span="7" class="roll">
				<err-list></err-list>

			</el-col>
		</el-row>
		<el-row :gutter="10" class="row_list order_list">
			<el-col :span="7">
				<pie-chart type="ordertype"></pie-chart>
			</el-col>
			<el-col :span="10">
				<column-chart></column-chart>
			</el-col>
			<el-col :span="7">
				<comment-list></comment-list>
			</el-col>
		</el-row>




	</section>
</template>

<script>

import salesTable from "./components/salesTable";  // 销售数据表格
import commentList from "cps/echarts/commentList";  // 用户评论列表
import cardList from "./components/cardList";  // card列表
import logList from "./components/logList";  // 基本信息
import errList from './components/errList' // 异常记录
import barChart from 'cps/echarts/barChart' // K线
import pieChart from 'cps/echarts/pieChart' // 投资类型 饼状图
import ColumnChart from 'cps/echarts/ColumnChart' // 每日收益 柱状图


export default {
	data() {
		return {

		}
	},
	components: {
		salesTable,
		commentList,
		cardList,
		logList,
		barChart,
		pieChart,
		errList,
		ColumnChart
	},
	created() {
	},
	mounted() {
	},
	methods: {
	}
}
</script>

<style lang="less" scoped>
.data_section {
	margin: 20px;
	border-radius: 2px;

	.row_list {
		margin-bottom: 20px;

		.wrapper {}

		.row_base {
			padding: 10px;
			box-sizing: border-box;
			background: #F5F5F5;
			border-radius: 6px;
			height: 120px;
		}



		.leftItem-text {
			padding-top: 25px;

		}

		.roll {
			padding: 0 !important
		}
	}

	.order_list {
		.orderArea {
			width: 100%;
			height: 300px;
			background: #f9f9f9 !important;
			border-radius: 6px;
			box-sizing: border-box;
			padding: 10px;
			padding-top: 40px;
			overflow: hidden;
			border: 1px solid #e8e8e8;
		}

		.orderbarArea {
			height: 370px;
		}
	}

	.data_list {
		//background: #eeeff2;
		background: #fff;
		text-align: center;
		font-size: 14px;
		border-radius: 6px;
		padding: 10px;
		color: #000;
		height: 80px;
		border: 1px solid #eeeff2;

		.leftItem {
			align-items: start;
			justify-content: space-between;
			text-align: left;

			.text {
				width: 100%;
				border-bottom: 1px solid #C0C0C0 !important;
				color: #696969;
			}
		}

		.rightItem {
			width: 62px;
			display: flex;
			align-items: center;
			justify-content: center;

			.svg-icon {
				font-size: 30px;
			}
		}

		.number {
			font-size: 22px;
			font-weight: bold;

			.perTitle {
				font-size: 13px;
				margin-left: 5px;
			}
		}
	}

	.pay {
		.leftItem {
			justify-content: space-around;
		}
	}

}
</style>
