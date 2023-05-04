
<template>
    <div class="logContainer">
        <el-card class="box-card">
            <div slot="header" class="clearfix">
                <span>
                    <h4 class="h4">异常记录</h4>
                </span>

            </div>
            <div class="logArea el-scrollbar">

                <div class="item" v-for="(item, index) in logsData" :key="index">
                    <p class="timeArea">
                    <div class="wapper">
                        <a href="" class="title data" v-for="(citem, cindex) in item.data" :key="cindex"> {{ citem }}</a>
                    </div>
                    </p>

                </div>

            </div>
        </el-card>
    </div>
</template>
  
<script>
import logsData from "@/assets/datas/err.json";

export default {
    name: 'radarChart',
    data() {
        return {
            logsData: logsData.data,

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

        .h4 {
            color: #8A0000;
        }



    }

    .logArea {
        overflow: auto;
        height: 100%;

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

        .data {
            padding-left: 10px;
            color: #8A0000;
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
  
  