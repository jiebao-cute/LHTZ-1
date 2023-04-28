
<template>
  <div class="logContainer">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span>
          <h4>美国股票市场</h4>
        </span>

        <img :src="Arrowhead" class='langAvatar' alt="">
      </div>
      <div class="logArea el-scrollbar">
        <div class="item" v-for="(item, index) in logsData" :key="index">
          <p class="timeArea">
            <span class="title">日期：</span>
            <span class="title time">{{ item.createTime }}</span>
          </p>
          <div class="logContent">
            <p class="title">更新内容：</p>
            <ul class="logUl">
              <li v-for="(citem, cindex) in item.data" :key="cindex">{{ citem }}</li>
            </ul>
          </div>
        </div>
      </div>

    </el-card>
  </div>
</template>

<script>
import logsData from "@/assets/datas/logs.json";
import { github } from "@/utils/env";
import Arrowhead from "@/assets/img/Arrowhead.svg";
export default {
  name: 'logList',
  data() {
    return {
      logsData: logsData.data,
      github: github,
      Arrowhead: Arrowhead
    };
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
  }

  .item {
    .title {
      font-size: 13px;
    }

    .time {
      color: #87DE75;
    }

    .logContent {
      .logUl {
        padding-left: 30px;

        li {
          font-size: 12px;
          list-style: disc;
          line-height: 20px;
        }
      }
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

