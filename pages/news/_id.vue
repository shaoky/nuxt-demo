<template>
    <div>
        <web-header></web-header>
        <div class="wrap mt10">
            <left-nav :categorys="categorys" :config="config"></left-nav>
            <div class="main-body">
                <div class="main-title">
                    <h4>{{news.typeName}}</h4>
                    <span class="right">
                        <nuxt-link to="index">首页</nuxt-link> > <nuxt-link :to="{name: 'news-type-id', params: { id: news.typeId }}">{{news.typeName}}</nuxt-link>
                    </span>
                </div>
                <div class="main-content">
                    <div class="news-title">
                        <h1>{{news.title}}</h1>
                        <div class="info">
                            <span>来源：本站</span>
                            <span>时间：{{news.createTime}}</span>
                            <span>浏览：{{news.viewCount}}次</span>
                        </div>
                    </div>
                    <div class="news-content" v-html="news.content"></div>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { getNewsInfo, getWebConfig, getProductCategory } from '../../api/getData'
import webHeader from '../../components/web-header.vue'
import leftNav from '../../components/left-nav.vue'
import page from '../../components/page.vue'

export default {
    components: {
        webHeader,
        leftNav,
        page
    },
    data() {
        return {

        }
    },
    async asyncData({params}: any) {
        const categorys: any  = await getProductCategory({});
        const news: any = await getNewsInfo({id: params.id})
        const config: any = await getWebConfig()

        return {
            categorys,
            news: news.info,
            config
        }
    }
}

</script>

<style lang="less" scoped>
.news-title {
    padding-bottom: 15px;
    text-align: center;
    border-bottom: 1px dotted #DBDBDB;
    h1 {
        font-weight: 100;
        font-size: 20px;
    }
    .info {
        margin-top: 10px;
        span {
            margin-right: 20px;
        }
    }
}
.news-content {
    margin-top: 15px;
    line-height: 27px;
    font-size: 14px;
}
</style>
