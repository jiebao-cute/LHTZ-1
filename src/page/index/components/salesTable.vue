
<template>
  <div class="logContainer">
    <el-card class="box-card">
      <div slot="header" class="clearfix">
        <span class="text">
          <h4>业绩表现</h4>
        </span>
      </div>
      <div class="logArea el-scrollbar">
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
import scoteData from "@/assets/datas/scote.json";
import Arrowhead from "@/assets/img/Arrowhead.svg";
export default {
  name: 'logList',
  data() {
    return {
      logsData: scoteData.data,
      Arrowhead: Arrowhead,
    };
  },
  methods: {

  }
}
</script>

<style lang="less" scoped>
.logContainer {
  border-radius: 6px;
  padding: 0;
  background: #f9f9f9;
  box-sizing: border-box;
  height: 370px;
  max-height: 370px;
  overflow: hidden;
  border-bottom: 1px solid #e8e8e8;

  .clearfix {
    display: flex;
    align-items: center;
    justify-content: flex-start;
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
      color: #10110f;
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

