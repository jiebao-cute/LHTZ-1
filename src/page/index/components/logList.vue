
<template>
  <div class="logContainer">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>
          <h4>基本信息</h4>
        </span>
        <img :src="Arrowhead" class='langAvatar' alt="">
      </div>
      <div class="logArea el-scrollbar">
        <span class="titleTop">PSC策略为趋势策略，结合AI学习+风险控制为一体的综合性策略，预期年化收益28%</span>
        <div class="item" v-for="(item, index) in logsData" :key="index">
          <p class="timeArea">
          <div class="wapper">
            <span class="title time">{{ item.title }}</span>
            <span class="title data" v-for="(citem, cindex) in item.data" :key="cindex"> {{ citem }}</span>
          </div>
          </p>

        </div>

      </div>
    </el-card>
  </div>
</template>

<script>
import logsData from "@/assets/datas/logs.json";
import Arrowhead from "@/assets/img/Arrowhead.svg";
export default {
  name: 'logList',
  data() {
    return {
      logsData: logsData.data,
      Arrowhead: Arrowhead,
    };
  },
  methods: {

  }
}
</script>

<style lang="less" scoped>
.logContainer {
  padding: 10px;
  background: #f9f9f9;
  box-sizing: border-box;
  height: 370px;
  max-height: 370px;
  overflow: hidden;
  border-radius: 6px;

  .clearfix {
    display: flex;
    align-items: center;
    justify-content: flex-start;

    .langAvatar {
      padding-left: 100px;
      background-color: #fff;
      margin: 0 10px;
      width: 20px;
      height: 20px;
      // border-radius: 50%;
      //vertical-align: middle;
      display: inline-block;
    }


  }

  .logArea {
    overflow: auto;
    height: 100%;

    .titleTop {
      font-size: 13px;
      color: #1d4369;
    }

    .wapper {
      display: flex;
      justify-content: space-between;
      align-items: center;

    }
  }

  .item {
    .title {
      font-size: 13px;
    }

    .time {
      color: #10110f;
    }

    .data {
      color: #460b0b;
    }


  }
}

.clearfix:before,
.clearfix:after {
  display: table;
  content: "";
}

.clearfix:after {
  clear: both
}
</style>

