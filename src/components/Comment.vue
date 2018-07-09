<template>
  <div class="comment">
    <div class="write_com">
      <input type="text" name="" value="" placeholder="写评论" />
      <img src="../assets/write_comment.png" alt="">
    </div>
    <div class="share_com">
      <template v-if="comment">
        <!--当前展开评论时-->
        <p @click="showIcon" class="content_icon">
          <img src="../assets/17_backnews.png" alt="">
          <strong>正文</strong>
        </p>
      </template>
      <template v-else>
        <p @click="showComment">
          <!--评论隐藏时-->
          <img src="../assets/13_comment.png" alt="" class="default_comment">
          <img src="../assets/46_dark_comment.png" alt="" class="dark_comment">
          <span>12</span>
        </p>
        <p @click="collect">
          <img :src="coll" alt="">
        </p>
      </template>
      <p @click="shareTo">
        <img src="../assets/13_share.png" alt="" class="default_share">
        <img src="../assets/47_dark_share.png" alt="" class="dark_share">
      </p>
    </div>
    <el-share :show="share" @hideShare="hideShare"></el-share>
  </div>
</template>

<script>
import Share from "@/components/Share";
export default {
  data() {
    return {
      coll: "static/images/14_collect.png",
      share: false,
      comment: false
    };
  },
  created() {
    if (document.getElementsByTagName("body")[0].className == "dark") {
      this.coll = "static/images/45_dark_collect.png";
    } else {
      this.coll = "static/images/14_collect.png";
    }
  },
  methods: {
    collect() {
      if (this.coll == "static/images/14_collect2.png") {
        if (document.getElementsByTagName("body")[0].className == "dark") {
          this.coll = "static/images/45_dark_collect.png";
        } else {
          this.coll = "static/images/14_collect.png";
        }
      } else {
        this.coll = "static/images/14_collect2.png";
      }
    },
    shareTo() {
      this.share = true;
    },
    hideShare() {
      this.share = false;
    },
    showComment() {
      this.comment = true;
      this.$emit("showComment");
    },
    showIcon() {
      this.comment = false;
      this.$emit("hideComment");
    }
  },
  components: {
    "el-share": Share
  }
};
</script>
