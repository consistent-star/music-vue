<template>
  <div class="home">
    <!--轮播图-->
    <el-carousel indicator-position="none" class="swiper-container" height="280px" arrow="always">
      <el-carousel-item v-for="(item, index) in swiperList" :key="index">
        <img :src="item.picImg" />
      </el-carousel-item>
    </el-carousel>
    <!--热门歌单-->
    <div class="section">
      <div class="section-title el-icon-s-help">
        <span>歌单</span>
        <div class="section-more">
          <span @click="goPath('/song-list')">更多</span>
          <i class="el-icon-right" @click="goPath('/song-list')"></i>
        </div>
      </div>
      <content-list :contentList="songList" path="song-list-album"></content-list>
    </div>
    <!--热门歌手-->
    <div class="section">
      <div class="section-title el-icon-s-help">
        <span>歌手</span>
        <div class="section-more">
          <span @click="goPath('/singer')">更多</span>
          <i class="el-icon-right" @click="goPath('/singer')"></i>
        </div>
      </div>
      <content-list :contentList="singerList" path="singer-album"></content-list>
    </div>
  </div>
</template>

<script>
import ContentList from "../components/ContentList";
import { swiperList } from "../assets/data/swiper";
import { HttpManager } from "../api/index";

export default {
  name: "home",
  components: {
    ContentList,
  },
  data() {
    return {
      swiperList: swiperList, // 轮播图列表
      songList: [], // 歌单列表
      singerList: [], // 歌手列表
    };
  },
  created() {
    // 获取歌单列表
    this.getSongList();
    // 获取歌手列表
    this.getSingerList();
  },
  methods: {
    goPath(path, value) {
      this.$router.push({ path: path });
    },
    getSongList() {
      HttpManager.getSongList()
        .then((res) => {
          this.songList = res.sort().slice(20, 30);
        })
        .catch((err) => {
          console.log(err);
        });
    },
    getSingerList() {
      HttpManager.getAllSinger()
        .then((res) => {
          this.singerList = res.sort().slice(15, 25);
        })
        .catch((err) => {
          console.log(err);
        });
    },
  },
};
</script>

<style lang="scss" scoped>
@import "../assets/css/home.scss";
</style>
