<template>
    <header class="head-nav rflex " :style="{ 'width': headNavWidth + 'px' }" id='header_container'>
        <div class="right-nav" ref="rightNav">
            <top-menu></top-menu>

            <div class="userinfo-right rflex">
                <div class="notify-row time">
                    {{ nowTime }}
                </div>

                <div class="userinfo">
                    <el-menu class="el-menu-demo" mode="horizontal" active-text-color="#fff " text-color="#fff"
                        background-color="#23282f">
                        <el-submenu index="1" popper-class="langItem">
                            <template slot="title">
                                <img :src="langLogo" class='langAvatar' alt="">
                            </template>
                            <el-menu-item index="1-1" @click="changeLocale('zh')">
                                <img :src="chinaImg" class='langAvatar' alt="">
                                <span class="intro">中文</span>
                            </el-menu-item>
                            <el-menu-item index="1-2" @click="changeLocale('en')">
                                <img :src="americaImg" class='langAvatar' alt="">
                                <span class="intro">EngList</span>
                            </el-menu-item>
                        </el-submenu>

                        <el-submenu index="2" popper-class="infoItem">
                            <template slot="title">
                                <div class='welcome'>
                                    <span class="name">{{ $t('commons.hi') }},</span>
                                    <span class='name avatarname'> {{ $t(`commons.${name}`) }}</span>
                                </div>
                                <img :src="userImg" class='avatar' alt="">
                            </template>
                            <el-menu-item index="2-3" @click="setDialogInfo('logout')">{{ $t('commons.quit')
                            }}</el-menu-item>
                        </el-submenu>
                    </el-menu>
                </div>
            </div>
        </div>
    </header>
</template>

<script>
import { mapGetters } from "vuex";
import { setToken, getToken } from '@/utils/auth'
import topMenu from "./topMenu";
import logoImg from "@/assets/img/logo.png";
import chinaImg from "@/assets/img/china.svg";
import americaImg from "@/assets/img/america.svg";
import userImg from "@/assets/img/admin.png";

export default {
    name: 'head-nav',
    data() {
        return {
            timer: "", //定义一个定时器
            nowTime: "",
            logo: logoImg,
            langLogo: getToken('langLogo') || americaImg,
            chinaImg: chinaImg,
            americaImg: americaImg,
            userImg: userImg,
            menu: {
                userBgcolor: '#f0f2f5'
            },
        }
    },
    components: {
        topMenu
    },
    computed: {
        ...mapGetters(['name', 'avatar', 'sidebar']),
        headNavWidth() {
            return document.body.clientWidth - this.sidebar.width
        },

    },
    created() {
        this.getTime()
    },
    beforeDestroy() {
        if (this.timer) {
            clearInterval(this.timer);
        }
    },
    methods: {
        logout() {
            this.$store.dispatch('LogOut').then(() => {
                location.reload();
            })
        },
        /**
        * 弹出框-修改密码或者系统设置   
        * @param {string} cmditem 弹框类型
        */
        setDialogInfo(cmditem) {
            switch (cmditem) {
                case 'info':
                    this.$router.push('/infoManage/infoShow/infoShow1');
                    break;
                case 'pass':
                    this.$router.push('/infoManage/infoModify/infoModify1');
                    break;
                case 'logout':
                    this.logout();
                    break;
            }
        },
        // 切换语言
        changeLocale(type) {
            setToken('lang', type);
            this.$i18n.locale = type;
            if (type === 'en') {
                this.langLogo = this.americaImg;
            } else {
                this.langLogo = this.chinaImg;
            }
            setToken('langLogo', this.langLogo);
        },
        //顶部时间
        getTime() {
            this.timer = setInterval(() => {
                let timeDate = new Date();
                let year = timeDate.getFullYear();
                let mounth = timeDate.getMonth() + 1;
                let day = timeDate.getDate();
                let hours = timeDate.getHours();
                hours = hours >= 10 ? hours : "0" + hours;
                let minutes = timeDate.getMinutes();
                minutes = minutes >= 10 ? minutes : "0" + minutes;
                let seconds = timeDate.getSeconds();
                seconds = seconds >= 10 ? seconds : "0" + seconds;
                let week = timeDate.getDay();
                let weekArr = [
                    "星期日",
                    "星期一",
                    "星期二",
                    "星期三",
                    "星期四",
                    "星期五",
                    "星期六",
                ];
                this.nowTime = `${year}/${mounth}/${day} ${hours}:${minutes}:${seconds} ${weekArr[week]}`
            }, 1000);
        },

    }

}
</script>

<style scoped lang='less'>
.right-nav {
    display: flex;
    flex: 1;
    width: calc(100% - 180px);
    padding-right: 15px;
    justify-content: space-between;
    box-shadow: 0px 2px 5px 0px rgba(237, 233, 233, 0.5);
}

.head-nav {
    position: fixed;
    top: 0;
    right: 0;
    z-index: 29;
    transition: width .2s;
    justify-content: space-between;

    height: 60px;
    box-sizing: border-box;
    background: #23282f;

    .logout {
        vertical-align: middle;
        cursor: pointer;
    }
}

.middle {
    align-items: center;
    border: 1px solid;
}

.userinfo-right {
    background: #23282f;
    width: 390px;
    padding: 0 10px;
    justify-content: space-between;
}

.time {
    color: #fff;
    padding-top: 2px;
    line-height: 20px;
    text-align: center;
    font-size: 12px;
    font-weight: bolder;
}

.userinfo {
    line-height: 60px;
    text-align: right;
}

/deep/ .el-menu-demo {
    background: #23282f;
}

.el-submenu {
    padding-left: 23px;
}

.is-opened {
    background: #23282f;
}

.avatar {
    background: #23282f;
    width: 32px;
    height: 32px;
    border-radius: 50%;
    vertical-align: middle;
    display: inline-block;
}

.langAvatar {
    background-color: #fff;
    margin: 0 10px;
    width: 24px;
    height: 24px;
    border-radius: 50%;
    vertical-align: middle;
    display: inline-block;
}

.welcome {
    display: inline-block;
    vertical-align: middle;
    padding: 0 5px;

    .name {
        color: #fff;
        line-height: 20px;
        text-align: center;
        font-size: 12px;
        font-weight: bolder;
    }

    .avatarname {
        color: #fff;
        font-weight: bolder;
        font-size: 13px;


    }
}

.username {
    cursor: pointer;
    margin-right: 5px;
}

.border {
    border: 1px solid;
}

.notify-row {
    line-height: 60px;
    flex: 1;
}

ul.top-menu>li {
    position: relative;
}
</style>
