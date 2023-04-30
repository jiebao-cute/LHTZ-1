
<template>
    <div class="logContainer">
        <el-card class="box-card">
            <div slot="header" class="clearfix">
                <span>
                    <h4 class="h4">异常记录</h4>
                </span>
                <img :src="Arrowhead" class='langAvatar' alt="">
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
import Arrowhead from "@/assets/img/Arrowhead.svg";
export default {
    name: 'radarChart',
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
    background: #f5f1f1;
    box-sizing: border-box;
    height: 300px;
    max-height: 370px;
    overflow: hidden;
    border-radius: 6px;

    .clearfix {
        display: flex;
        align-items: center;
        justify-content: flex-start;

        .h4 {
            color: #8A0000;
        }

        .langAvatar {
            padding-left: 100px;
            background-color: #f4f4f4;
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
  
  