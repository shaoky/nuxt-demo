<template>
    <div class="header">
        <div class="welcome">欢迎来到某某某公司</div>
        <div class="top">
            <div class="logo">
                某某公司Logo1
            </div>
            <div class="contact">
                电话：18788889999
            </div>
        </div>
        <div class="nav">
            <div class="item" v-for="(item, index) in list" :key="index">
                <nuxt-link :to="item.url">{{item.title}}</nuxt-link>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
export default {
    data() {
        return {
            list: [
                {
                    title: '首页',
                    url: '/'
                },
                {
                    title: '公司简介',
                    url: '/company'
                },
                {
                    title: '产品中心',
                    url: '/product/type/0'
                },
                {
                    title: '新闻中心',
                    url: '/news/type/3'
                },
                {
                    title: '行业资讯',
                    url: '/news/type/2'
                },
                {
                    title: '联系我们',
                    url: '/contact'
                }
            ]
        }
    }
}
</script>

<style lang="less" scoped>
.header {
    width: 1000px;
    height: 194px;
    margin: 0 auto;
    .welcome {
        height: 30px;
        line-height: 30px;
    }
    .top {
        height: 119px;
        .logo {
            width: 200px;
            float: left;
        }
        .contact {
            float: right;
        }
        &::after {
            // clear: both;
        }
    }
    .nav {
        display: flex;
        align-items: center;
        height: 45px;
        color: #fff;
        font-size: 14px;
        .item {
            width: 150px;
            line-height: 45px;
            background: url('/nav-item-bg.jpg') right no-repeat;
            text-align: center;
            a {
                display: block;
                text-decoration: none;
                color: #fff;
            }
            &:last-child {
                background: none;
            }
        }
    }
}
</style>
