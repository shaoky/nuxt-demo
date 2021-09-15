<template>
    <div>
        <web-header></web-header>
        <div class="wrap mt10">
            <left-nav :categorys="categorys" :config="config"></left-nav>
            <div class="main-body">
                <div class="main-title">
                    <h4>{{goodsClassName || '产品中心'}}</h4>
                    <span class="right">
                        <nuxt-link to="index">首页</nuxt-link> > {{goodsClassName}}
                    </span>
                </div>
                <div class="main-content">
                    <div class="item" v-for="item in products" :key="item.id">
                        <div class="item-img">
                            <el-image 
                                style="max-width: 100%; height: 168px"
                                :src="item.imageUrl" 
                                :preview-src-list="srcList">
                            </el-image>
                        </div>
                        <div class="item-title">
                            {{item.title}}
                        </div>
                    </div>
                    <div class="clear"></div>

                    <div class="demo-image__preview">
                        
                    </div>
                    <page class="mt20"></page>
                </div>
            </div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { getProducts, getWebConfig, getProductCategory } from '../../../api/getData'
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
        return {}
    },
    async asyncData({params}: any) {
        const categorys: any  = await getProductCategory({});
        const product: any = await getProducts({type: params.id})
        const config: any = await getWebConfig()
        const srcList = product.list.map((item: any) => item.imageUrl)
        
        return {
            categorys,
            products: product.list,
            config,
            goodsClassId: params.id,
            goodsClassName: product.goodsClassName,
            srcList
        }
    }
}

</script>

<style lang="less" scoped>
.item {
    float: left;
    width: 190px;
    padding: 5px 10px;
    margin-right: 35px;
    &:nth-child(3n) {
        margin-right: 0;
    }
}
.item-img {
    width: 100%;
    height: 168px;
    border: 1px solid #ccc;
    img {
        max-width: 100%;
        height: 100%;
        display: inline-block;
    }
}
.item-title {
    margin-top: 5px;
    display: block;
    text-align: center;
    line-height: 25px;
}

.el-image {
    display: flex;
    align-items: center;
}
/deep/.el-image__error, .el-image__inner, .el-image__placeholder {
    max-width: 100%!important;
}
</style>
