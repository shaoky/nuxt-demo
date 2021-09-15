<template>
    <div>
        <web-header></web-header>
        <div class="wrap mt10">
            <left-nav :categorys="categorys" :config="config"></left-nav>
            <div class="main-body">
                <div class="main-title">
                    <h4>联系我们</h4>
                    <span class="right">
                        <nuxt-link to="index">首页</nuxt-link> > 联系我们
                    </span>
                </div>
                <div class="main-content">
                <baidu-map
                    id="allmap" 
                    class="bm-view" 
                    :center="center" 
                    :zoom="zoom" 
                    :scroll-wheel-zoom="true" 
                    @click="mapClick"
                    ak="O3aiwCPwChwQFcEoXXu0nzuS315TtqW8">
                    <bm-navigation anchor="BMAP_ANCHOR_TOP_RIGHT"></bm-navigation>
                    <bm-marker :position="center" :dragging="true" @click="infoWindowOpen"></bm-marker>
                    <!-- animation="BMAP_ANIMATION_BOUNCE" -->
                    <!-- <bm-info-window :position="center" :show="false"  @close="infoWindowClose" @open="infoWindowOpen">
                    <p>{{config.webTitle}}</p>
                    <p>联系人：{{config.linkman}}</p>
                    <p>手机：{{config.tel}}</p>
                    <p>地址：{{config.address}}</p>
                    </bm-info-window> -->
                </baidu-map>
                </div>
            </div>
        </div>
    </div>
</template>
<script lang="ts">
import Vue from 'vue'
import { getProductCategory, getWebConfig, getNewsInfo } from '../api/getData'
import webHeader from '../components/web-header.vue'
// import BaiduMap from 'vue-baidu-map/components/map/Map.vue'

export default ({
    data() {
        return {
            zoom: 13,
            content: '11111111',
            show: false
        }
    },
    components: {
        webHeader,
        // BaiduMap
    },
    async asyncData(context: any) {
        const categorys: any  = await getProductCategory({})
        const config: any = await getWebConfig()
        const center = {
            lng: config.baiduMapX,
            lat: config.baiduMapY
        }
        return {
            categorys,
            config,
            center
        }
    },
    methods: {
        infoWindowOpen() {
        // @ts-ignore
        this.show = true
        },
        infoWindowClose () {
        // @ts-ignore
        this.show = false
        },
        mapClick(e: any) {
        console.log(e)
        }
    }
})
</script>

<style lang="less" scoped>
.main-content {
    line-height: 27px;
}
.bm-view {
    width: 100%;
    height: 400px;
}
</style>
