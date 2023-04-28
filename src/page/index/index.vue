<template>
	<section class="data_section" ref="data_section">
		<el-row :gutter="10" class="row_list">
			<el-col :span="8">
				<div class="row_left row_base">
					<el-col :span="14">
						<div class="pay saleBgcolor data_list rflex">
							<div class="leftItem cflex wflex">
								<p class="investor">{{ $t('index.yearLoss') }}</p>
								<p class="number">68<span class="perTitle">({{ $t('index.tenMillion') }})</span></p>
							</div>
							<div class="rightItem">
								<icon-svg icon-class="iconfukuan" />
							</div>
						</div>
					</el-col>
					<el-col :span="10">
						<div class="pay taxBgcolor data_list rflex">
							<div class="leftItem cflex wflex">
								<p class="investor">{{ $t('index.yearProfit') }}</p>
								<p class="number">120<span class="perTitle">(%)</span></p>
							</div>

						</div>
					</el-col>
				</div>
			</el-col>
			<el-col :span="16">
				<div class="row_right row_base">
					<el-col :span="1">
						<div class="leftItem-text">
							<div class="">
								<h4>市</h4>
							</div>
							<div class="">
								<h4>场</h4>
							</div>
							<div class="">
								<h4>资</h4>
							</div>
							<div class="">
								<h4>讯</h4>
							</div>
						</div>
					</el-col>
					<el-col :span="23">
						<div class="extenedBgcolor data_list rflex">
							<div class="leftItem cflex wflex">
								<div class="investor text">{{ $t('index.potentialInvestor') }}</div>
								<div class="text">OMV 利润下降，警告产量下降,OMV 利润下降，警告产量下降, </div>
								<div class="text">日本央行维持宽松政策，将重新审视货币政策，将重新审视货币政策</div>
							</div>
						</div>
					</el-col>

				</div>
			</el-col>
		</el-row>
		<el-row :gutter="10" class="row_list order_list">
			<el-col :span="7">
				<log-list></log-list>
			</el-col>
			<el-col :span="17">
				<bar-chart type="barChart"></bar-chart>
			</el-col>
		</el-row>
		<el-row :gutter="10" class="row_list order_list">
			<el-col :span="7">
				<pie-chart type="ordertype"></pie-chart>
			</el-col>
			<el-col :span="10">
				<line-chart></line-chart>
			</el-col>
			<el-col :span="7">
				<radar-chart></radar-chart>
			</el-col>
		</el-row>
		<el-row :gutter="10" class="row_list">
			<el-col :span="11">
				<sales-table></sales-table>
			</el-col>
			<el-col :span="7">
				<comment-list></comment-list>
			</el-col>
			<el-col :span="6">
				<card-list></card-list>
			</el-col>
		</el-row>

	</section>
</template>

<script>
import echarts from 'echarts'
import salesTable from "./components/salesTable";  // 销售数据表格
import commentList from "./components/commentList";  // 用户评论列表
import cardList from "./components/cardList";  // card列表
import logList from "./components/logList";  // 日志列表
import barChart from 'cps/echarts/barChart' // 用户投资类型 柱状图
import pieChart from 'cps/echarts/pieChart' // 用户投资类型 饼状图
import radarChart from 'cps/echarts/radarChart' // 用户投资类型 雷达图
import lineChart from 'cps/echarts/lineChart' // 用户投资类型 折线图
import { github } from "@/utils/env";

export default {
	data() {
		return {
			github: github
		}
	},
	components: {
		salesTable,
		commentList,
		cardList,
		logList,
		barChart,
		pieChart,
		radarChart,
		lineChart
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

		.row_base {
			padding: 10px;
			box-sizing: border-box;
			background: #fff;
			border-radius: 6px;
			height: 120px;
		}

		.leftItem-text {
			padding-top: 4px;
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
