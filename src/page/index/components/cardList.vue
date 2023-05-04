<template>
  <div class="productProcess">
    <div class="title_div">
      产品监控
    </div>
    <div class="success_info_body" v-show="showFlag">

      <!-- 参数名称、列数根据实际情况调整 -->
      <div class="table_body">
        <div class="table_th">
          <div class="tr1 th_style">代码</div>
          <div class="tr2 th_style">名称</div>
          <div class="tr3 th_style">交易数量</div>
          <div class="tr4 th_style">成交状况</div>
        </div>
        <div class="table_main_body">
          <div class="table_inner_body" :style="{ top: tableTop + 'px' }">
            <div class="table_tr" v-for="(item, index) in tableList" :key="index">
              <div class="tr1 tr">{{ item.planNo }}</div>
              <div class="tr2 tr">{{ item.type }}</div>
              <div class="tr3 tr">{{ item.DateMoney }}</div>
              <div class="tr4 tr">{{ item.process }} </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import tradeData from "@/assets/datas/trade.json";
export default {
  name: 'cardList',
  data() {
    return {
      //是否显示页面
      showFlag: true,
      //记时器
      tableTimer: null,
      tableTop: 0,
      tableList: tradeData.data,
      tableListSize: 0,
      componentTimer: null,

      //需要根据情况设置的参数
      visibleSize: 6, //容器内可视最大完整行数
      lineHeight: 49, //每行的实际高度（包含margin-top/bottom,border等）
      componentTimerInterval: 3600000, //刷新数据的时间间隔
      tableTimerInterval: 100 //向上滚动 1px 所需要的时间，越小越快，推荐值 100
    };
  },

  //如果没有父元素传值，将watch内的内容搬至mounted中即可
  props: ["activeFactoryId"],
  watch: {
    activeFactoryId(val, oldVal) {
      clearInterval(this.componentTimer);
      this.bsGetProductProcess();
      this.componentTimerFun();
    }
  },
  mounted() {
    this.tableActionFun();
  },
  beforeDestroy() {
    clearInterval(this.componentTimer);
    clearInterval(this.tableTimer);
  },
  methods: {
    //调用数据接口，获取列表数据，根据自己情况填接口url
    // bsGetProductProcess() {
    //   clearInterval(this.tableTimer);
    //   this.tableTop = 0;
    //   if (this.activeFactoryId != "") {
    //     this.showFlag = false;
    //     this.$ajax({
    //       method: "get",
    //       url: `` //根据自己情况填接口url
    //     })
    //       .then(res => {
    //         this.tableList = res.data.data;
    //         this.showFlag = true;
    //         this.tableActionFun();
    //       })
    //       .catch(function (err) {
    //         console.log("bsGetProductProcess error!");
    //       });
    //   }
    // },
    tableActionFun() {
      this.tableListSize = this.tableList.length;
      //如果数据长度超出容器最大容量
      if (this.tableListSize > this.visibleSize) {
        this.tableList = this.tableList.concat(this.tableList);
        this.tableTimerFun();
      } else {
        this.fillTableList();
      }
    },
    //当数据过少时，不触发自动轮播事件，并填充没有数据的行，参数根据实际情况修改即可
    fillTableList() {
      var addLength = this.visibleSize - this.tableListSize;
      for (var i = 0; i < addLength; i++) {
        this.tableList.push({
          planNo: "-",
          type: "-",
          startDate: "-",
          endDate: "-",
          process: "-"
        });
      }
    },
    tableTimerFun() {
      var count = 0;
      this.tableTimer = setInterval(() => {
        if (count < (this.tableList.length / 2) * this.lineHeight) {
          this.tableTop -= 1;
          count++;
        } else {
          count = 0;
          this.tableTop = 0;
        }
      }, this.tableTimerInterval);
    },
    componentTimerFun() {
      this.componentTimer = setInterval(() => {
        this.bsGetProductProcess();
      }, this.componentTimerInterval);
    }
  }
};
</script>

<style scoped>
.productProcess {
  background: #f9f9f9;
  border-radius: 6px;
  height: 369px;
  border: 1px solid #e3e3e3;
  margin-right: 5px !important;
}

.title_div {
  border-radius: 6px;
  background: #e3e3e3;
  width: 100%;
  text-align: center;
  font-weight: bold;
}

.table_body {
  width: 100%;
  margin-top: 1px;
}

.table_th {
  width: 100%;
  display: flex;
  height: 40px;
  line-height: 40px;
}

.tr {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  box-sizing: border-box;

  text-align: center;
  font-size: 14px;
}

.tr1 {
  width: 28%;
}

.tr2 {
  width: 15%;
}

.tr3 {
  width: 35%;
  font-size: 13px;
}

.tr4 {
  flex: 1;
}

.th_style {
  color: rgb(83, 113, 117);
  font-weight: bold;
  font-size: 16px;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  box-sizing: border-box;
  padding: 0 2px;
  text-align: center;
}

.table_main_body {
  width: 100%;
  height: 294px;
  overflow: hidden;
  position: relative;
}

.table_inner_body {
  width: 100%;
  position: absolute;
  left: 0;
}

.table_tr {

  display: flex;
  height: 20px;
  line-height: 20px;
  color: #000000;
  font-size: 10px;

  margin-top: 7px;
}
</style>
