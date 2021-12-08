<template>
  <div class="content-list">
    <ul class="section-content">
      <!-- <li class="content-item" v-for="(item, index) in contentList" :key="index">
        <div class="kuo" @click="goAblum(item)">
          <img class="item-img" :src="attachImageUrl(item.pic)" alt />
          <div class="mask" @click="goAblum(item)">
            <svg class="icon" aria-hidden="true">
              <use :xlink:href="BOFANG" />
            </svg>
          </div>
        </div>
        <p class="item-name">{{item.name || item.title}}</p>
      </li> -->
      <div
        class="ThemeCoverWrapper"
        v-for="(item, index) in contentList"
        :key="index"
        @click="goAblum(item)"
      >
        <div class="cover-top">
          <img class="item-img" :src="attachImageUrl(item.pic)" alt />
          <div class="cover sprite_cover">
            <div class="info sprite_cover">
              <i class="el-icon-video-play"></i>
            </div>
          </div>
        </div>
        <div class="cover-bottom text-nowrap item-name" >
          <span>{{item.name || item.title}}</span>
          <i v-if="item.name" class="el-icon-user-solid"></i>
          </div>
        <div class="cover-source text-nowrap" v-if="!item.name">类型：{{item.style}}</div>
      </div>
    </ul>
  </div>
</template>

<script>
import mixin from "../mixins";
import { ICON } from "../assets/icon/index";

export default {
  name: "content-list",
  mixins: [mixin],
  props: {
    contentList: Array,
    path: String,
  },
  data() {
    return {
      BOFANG: ICON.BOFANG,
    };
  },
  methods: {
    goAblum(item) {
      this.$store.commit("setTempList", item);
      this.$router.push({ path: `/${this.path}/${item.id}` });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/css/content-list.scss";
</style>
