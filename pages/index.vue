<template>
    <div>
        <web-header></web-header>
        <web-banner></web-banner>
        <div class="wrap">
            <div class="category"></div>
            <div class="products"></div>
            <div class="news"></div>
        </div>
    </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { getNews } from '../api/getData'
import webBanner from '../components/web-banner.vue'
import webHeader from '../components/web-header.vue'

export default {
    components: {
        webHeader,
        webBanner
    },
    data() {
        return {
        }
    },
    async asyncData(context: any) {
        const res: any = await getNews({type: 2})
        return {
            news: res.list
        }
    }
}

</script>

<style>

</style>
