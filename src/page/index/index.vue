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
					<el-col :span="3">
						<div class="leftItem-text">
							<div class="">
								<h4>Market
								</h4>
							</div>
							<div class="">
								<h4>News</h4>
							</div>
						</div>
					</el-col>
					<el-col :span="21">
						<div class="extenedBgcolor data_list rflex">
							<div class="leftItem cflex wflex">
								<div class="investor text">ProSiebenSat.1 Tumbles on Outlook, Dividend News</div>
								<div class="text">French Economy Expands Slightly, as Expected </div>
								<div class="text">ProSiebenSat.1 Tumbles on Outlook, Dividend News</div>
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
				<err-list></err-list>
			</el-col>
		</el-row>
		<el-row :gutter="10" class="row_list">
			<el-col :span="6">
				<sales-table></sales-table>
			</el-col>
			<el-col :span="10">
				<comment-list></comment-list>
			</el-col>
			<el-col :span="8">
				<card-list></card-list>
			</el-col>
		</el-row>

	</section>
</template>

<script>

import salesTable from "./components/salesTable";  // 销售数据表格
import commentList from "./components/commentList";  // 用户评论列表
import cardList from "./components/cardList";  // card列表
import logList from "./components/logList";  // 基本信息
import errList from './components/errList' // 异常记录
import barChart from 'cps/echarts/barChart' // K线
import pieChart from 'cps/echarts/pieChart' // 投资类型 饼状图
import lineChart from 'cps/echarts/lineChart' // 每日收益 柱状图


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
			padding-top: 25px;

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
