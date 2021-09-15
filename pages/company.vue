<template>
  <div>
    <web-header></web-header>
    <div class="wrap mt10">
      <left-nav :categorys="categorys" :config="config"></left-nav>
      <div class="main-body">
        <div class="main-title">
          <h4>公司简介</h4>
          <span class="right">
            <nuxt-link to="index">首页</nuxt-link> > 公司简介
          </span>
        </div>
        <div class="main-content" v-html="company.content">
          <!-- 　　温州同益包装有限公司位于享有“中国塑编城”“中国信用第一镇”美誉的萧江，是一家从事塑料、编织产品研发、生产、贸易的民营企业。公司主要经营：塑料编织袋、复合袋制造、加工、销售；货物进出口、技术进出口。我们有最好的产品和专业的销售和技术团队，在公司发展的几年里，我们为客户提供最好的产品、良好的技术支持、健全的售后服务。   -->
<!-- 　　温州同益包装有限公司是温州包装行业知名企业，产品销往全国各地，公司以诚信的理念、科学的管理，将企业做大做强。公司注重科学管理，不断技术创新，努力降低成本。如果您对我公司的产品服务有兴趣，请在线留言或者来电咨询。 -->
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import { getProductCategory, getWebConfig, getNewsInfo } from '../api/getData'
import webHeader from '../components/web-header.vue'

export default ({
  components: {
    webHeader
  },
  async asyncData(context: any) {
    const categorys: any  = await getProductCategory({});
    const config: any = await getWebConfig()
    const company: any = await getNewsInfo({ id: 6 })
    return {
      categorys,
      config,
      company: company.info
    }
  }
})
</script>

<style lang="less" scoped>
.main-content {
  line-height: 27px;
}
</style>
