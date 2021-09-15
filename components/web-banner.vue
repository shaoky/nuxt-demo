<template>
    <div class="banner">
        <el-carousel indicator-position="outside" height="450px">
            <el-carousel-item v-for="(item, index) in list" :key="index">
                <img :src="item.imageUrl" alt="">
            </el-carousel-item>
        </el-carousel>
    </div>
</template>
<script lang="ts">
export default {
    data() {
        return {
            list: [
                {
                    imageUrl: '/b01.jpg',
                    url: '/'
                },
                {
                    imageUrl: '/b02.jpg',
                    url: '/'
                },
                {
                    imageUrl: '/b03.jpg',
                    url: '/'
                },
            ]
        }
    }
}
</script>

<style lang="less" scoped>
.banner {
   max-width: 1440px;
   height: 450px;
   margin: 0 auto;
}
</style>
