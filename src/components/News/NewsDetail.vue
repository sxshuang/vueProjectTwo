<template>
  <div class="tmpl">
    <nav-bar title="新闻详情"></nav-bar>
    <div class="news-title">
      <p>{{newsDetail.title}}</p>
      <div>
        <span>{{newsDetail.click}}</span>
        <span>分类：民生经济</span>
        <span>添加时间：{{newsDetail.add_time | convertTime('YYYY年MM月DD日')}}</span>
      </div>
    </div>
    <div class="news-content" v-html="newsDetail.content"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      newsDetail: {} //新闻详情
    };
  },
  created() {
    // 获取路由查询字符串参数id
    let id = this.$route.query.id;
    this.$axios
      .get("getnew/" + id)
      .then(res => {
        this.newsDetail = res.data.message[0];
      })
      .catch(err => console.log(err));
  }
};
</script>

<style scoped>
.news-title p {
  color: #0a87f8;
  font-size: 20px;
  font-weight: bold;
}
.news-title span {
  margin-right: 30px;
}
.news-title {
  margin-top: 5px;
  border-bottom: 1px solid rgb(0, 0, 0, 0.2);
}

/* 主题文章的左右距离 */
.news-content {
  padding: 10px 5px;
}


</style>


