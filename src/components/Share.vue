<template>
  <div class="share" v-if="show">
    <div class="share_cont">
      <ul>
        <li>
          <img src="../assets/wechat.png" alt="" class="default_share_icon">
          <img src="../assets/50_dark_share_wechat.png" alt="" class="dark_share_icon">
          <p>微信</p>
        </li>
        <li>
          <img src="../assets/friend.png" alt="" class="default_share_icon">
          <img src="../assets/49_dark_share_wechat.png" alt="" class="dark_share_icon">
          <p>朋友圈</p>
        </li>
        <li>
          <img src="../assets/sina.png" alt="" class="default_share_icon">
          <img src="../assets/51_dark_-share_sina.png" alt="" class="dark_share_icon">
          <p>新浪微博</p>
        </li>
        <li>
          <img src="../assets/qq.png" alt="" class="default_share_icon">
          <img src="../assets/52_dark_share_qq.png" alt="" class="dark_share_icon">
          <p>QQ</p>
        </li>
        <li>
          <div class="share_icon"></div>
          <p>敬请期待</p>
        </li>
        <li>
          <div class="share_icon"></div>
          <p>敬请期待</p>
        </li>
      </ul>
      <p class="cancel" @click="cancel">取消</p>
    </div>
  </div>
</template>

<script>
export default {
  props: ["show"],
  methods: {
    cancel() {
      this.$emit("hideShare");//把子组件的数据传给父组件)s
    }
  }
};
</script>
