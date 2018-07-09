<template>
    <div class="like_wrap">
        <div class="msg_header">
          <h2>赞过的评论</h2>
          <img src="../assets/back.png" alt="" @click="backMine" class="default_back">
          <img src="../assets/dark_back.png" alt="" @click="backMine" class="dark_back">
        </div>
        <ul class="like_list">
          <li>
            <img src="../assets/img_54X54.png" alt="">
            <div>
              <h3>
                <strong>甲甲甲</strong>
              </h3>
              <p>谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工。</p>
            </div>
          </li>
          <li>
            <img src="../assets/img_54X54.png" alt="">
            <div>
              <h3>
                <strong>乙乙乙</strong>
              </h3>
              <p>谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工。</p>
            </div>
          </li>
          <li>
            <img src="../assets/img_54X54.png" alt="">
            <div>
              <h3>
                <strong>丙丙丙</strong>
              </h3>
              <p>谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工。</p>
            </div>
          </li>
        </ul>
        <p class="all_content">已显示全部内容</p>
    </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    backMine() {
      this.$router.push("my");
    }
  }
};
</script>
