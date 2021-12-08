<template>
  <div class="the-footer">
    <!-- <p v-for="(item, index) in footerList" :key="index">
      {{item}}
    </p> -->
    <div class="left FooterLeft">
       <div class="copyright">
         <span>森屿公司版权所有©2021-2121</span>
         <span>
           西邮森屿科技有限公司运营：
           <a href="https://p1.music.126.net/Mos9LTpl6kYt6YTutA6gjg==/109951164248627501.png" rel="noopener noreferrer" target="_blank">陕[2021]1905号</a>
         </span>
       </div>
       <div class="report">
         <span>违法和不良信息举报电话：000-00000000</span>
         <span>
           举报邮箱：
           <a href="123456789@qq.com" target="_blank" rel="noopener noreferrer">123456789@163.com</a>
         </span>
       </div>
       <div class="info">
         <span>陕B1-123456-19</span>
         <a href="http://www.beian.miit.gov.cn/publish/query/indexFirst.action" rel="noopener noreferrer" target="_blank">
           工业和信息化部备案管理系统网站
         </a>
       </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'the-footer',
  data () {
    return {
      footerList: [
        `关于 | 帮助 | 条款 | 反馈`,
        `Copyright © 2019 Yin-Hongwei`
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
@import '../assets/css/the-footer.scss';
</style>
