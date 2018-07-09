<template>
<div class="nav">
    <div class="default_nav">
      <router-link to="/home" class="nav_item">
          <img src="../assets/news_on.png" v-if="index==1" />
          <img src="../assets/news.png" v-else />
          <p>新闻</p>
      </router-link>
      <router-link to="/sub" class="nav_item">
          <img src="../assets/sub_on.png" v-if="index==2" />
          <img src="../assets/sub.png" v-else />
          <p>订阅</p>
      </router-link>
      <router-link to="/my" class="nav_item">
          <img src="../assets/mine_on.png" v-if="index==3" />
          <img src="../assets/mine.png" v-else />
          <p>我</p>
      </router-link>
    </div>
    <div class="dark_nav">
      <router-link to="/home" class="nav_item">
          <img src="../assets/41_dark_news1.png" v-if="index==1" />
          <img src="../assets/41_dark_news2.png" v-else />
          <p>新闻</p>
      </router-link>
      <router-link to="/sub" class="nav_item">
          <img src="../assets/42_dark_order1.png" v-if="index==2" />
          <img src="../assets/42_dark_order2.png" v-else />
          <p>订阅</p>
      </router-link>
      <router-link to="/my" class="nav_item">
          <img src="../assets/43_dark_me1.png" v-if="index==3" />
          <img src="../assets/43_dark_me2.png" v-else />
          <p>我</p>
      </router-link>
    </div>
</div>
</template>

<script>
export default {
  props: ["index"]
};
</script>