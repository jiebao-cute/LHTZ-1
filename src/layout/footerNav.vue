<template>
    <div class='footer'>
        <p class="intro rflex">
            <span>{{ $t('commons.ai') }}Admin</span>

            <span>wdlhao2013({{ $t('commons.wechatNumber') }})</span>
        </p>
        <p class="beian">量化投资</p>
    </div>
</template>


<script>
import { github } from "@/utils/env";

export default {
    name: "footerNav",
    data() {
        return {
            github: github
        }
    },
    methods: {

    }
}
</script>

<style lang="less">
.footer {
    width: 100%;
    padding: 0;
    font-size: 12px;
    text-align: center;
    background: #23282f;

    p {
        color: #fff;
        line-height: 30px;
    }

    .intro {
        width: 240px;
        margin: 0 auto;
        justify-content: space-between;
        align-items: center;
    }
}
</style>


