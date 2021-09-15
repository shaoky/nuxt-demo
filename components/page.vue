<template>
    <el-pagination
        background
        layout="prev, pager, next"
        :total="total">
    </el-pagination>
</template>
<script lang="ts">
export default {
    props: {
        total: {
            type: Number,
            default: 1
        }
    }
}
</script>
<style lang="less" scoped>
.el-pagination {
    margin-top: 20px;
    text-align: center;
    font-weight: normal;
}
</style>
