<template>
    <div>
        <web-header></web-header>
        <div class="wrap mt10">
            <left-nav :categorys="categorys" :config="config"></left-nav>
            <div class="main-body">
                <div class="main-title">
                    <h4>{{articleTypeName}}</h4>
                    <span class="right">
                        <nuxt-link to="index">首页</nuxt-link> > <nuxt-link :to="{name: 'news-type-id', params: {id: id}}">{{articleTypeName}}</nuxt-link>
                    </span>
                </div>
                <div class="main-content">
                    <div class="item" v-for="item in news" :key="item.id">
                        <span></span>
                        <div class="title">
                            <nuxt-link :to="{name: 'news-id', params: {id: item.id}}">{{item.title}}</nuxt-link>
                        </div>
                        <div class="date">{{item.createTime}}</div>
                    </div>

                    <page></page>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { getNews, getWebConfig, getProductCategory } from '../../../api/getData'
import webHeader from '../../../components/web-header.vue'
import leftNav from '../../../components/left-nav.vue'
import page from '../../../components/page.vue'

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
        const news: any = await getNews({type: params.id})
        const config: any = await getWebConfig()

        return {
            categorys,
            news: news.list,
            config,
            articleTypeName: news.articleTypeName,
            id: params.id
        }
    }
}

</script>

<style lang="less" scoped>
.item {
    display: flex;
    align-items: center;
    height: 25px;
    padding: 5px 10px;
    border-bottom: 1px dashed #E4E4E4;
    span {
        width: 3px;
        height: 3px;
        margin-right: 10px;
        display: inline-block;
        background: rgb(1, 4, 9);
    }
    .title {
        flex: 1;
    }
}
</style>
