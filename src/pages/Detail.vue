<template>
  <div class="detail_wrap">
    <div class="msg_header">
      <h2></h2>
      <img src="../assets/back.png" alt="" @click="backMine" class="default_back">
      <img src="../assets/dark_back.png" alt="" @click="backMine" class="dark_back">
    </div>
    <div class="detail" v-if="network">
      <h2>谷歌官方出品：超轻量人工智能时代的创造</h2>
      <template v-if="comment">
        <!--评论未展开显示时-->
        <div class="sub_info">
          <div class="author">
            <img src="../assets/uc.png" alt="">
            <p>
              <strong>UC新闻</strong>
              <span><em>置顶</em>刚刚更新</span>
            </p>
          </div>
          <div :class="sub" @click="subscribe">订阅</div>
        </div>
        <div class="content">
          <p>虽然有很多利用语音识别技术的语音助手产品，但是大多数语音助手还不能够清晰识别出人类语言，并且回应很生硬。</p>
          <p>对于软件系统来说，掌握人类语言仍然是一个挑战。但是，据韩联社报道，近日谷歌工程师预测，人工智能（AI）技术将在五年内使人机对话成为可能。谷歌搜索质量工程师哈达尔·赛姆托（Ha-dar Shemtov）表示，谷歌正在运用自然语言处理技术（Natural Language Processing，简称NLP）技术，能够使机器与人类对话。</p>
          <p class="detail_img"><img src="../assets/img_690X270.png" alt=""></p>
          <p>对于软件系统来说，掌握人类语言仍然是一个挑战。但是，据韩联社报道，近日谷歌工程师预测，人工智能（AI）技术将在五年内使人机对话成为可能。谷歌搜索质量工程师哈达尔·赛姆托（Ha-dar Shemtov）表示，谷歌正在运用自然语言处理技术（Natural Language Processing，简称NLP）技术，能够使机器与人类对话。</p>
        </div>
      </template>
      <template v-else>
        <!--评论展开显示时-->
        <div class="comment_wrap">
          <div class="comment_info">
              <span><em>置顶</em>刚刚更新</span><strong>UC新闻</strong>
          </div>
          <p class="comment_num">全部评论(901)</p>
          <div class="no_comm" v-if="comments==0">
            <img src="../assets/56_no_comment.png" />
            <p>暂无评论</p>
          </div>
          <ul class="comment_list" v-else>
            <li>
              <img src="../assets/img_54X54.png" />
              <div>
                <p class="comm_title" :class="commList[0].curr">
                  <strong>卡卡唯</strong>
                  <!--likeGood点赞样式-->
                  <span class="comm_def" @click="likeGood(0)"><em>{{commList[0].num}}</em><img src="../assets/6_icon_good.png" /></span>
                  <span class="comm_active" @click="likeGood(0)"><em>{{commList[0].num}}</em><img src="../assets/6_icon_good2.png" /></span>
                </p>
                <p class="comm_content">谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工。</p>
                <p class="comm_time">4小时前</p>
              </div>
            </li>
            <li>
              <img src="../assets/img_54X54.png" />
              <div>
                <p class="comm_title" :class="commList[1].curr">
                  <strong>卡卡唯</strong>
                  <span class="comm_def" @click="likeGood(1)"><em>{{commList[1].num}}</em><img src="../assets/6_icon_good.png" /></span>
                  <span class="comm_active" @click="likeGood(1)"><em>{{commList[1].num}}</em><img src="../assets/6_icon_good2.png" /></span>
                </p>
                <p class="comm_content">谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工。</p>
                <p class="comm_time">4小时前</p>
              </div>
            </li>
            <li>
              <img src="../assets/img_54X54.png" />
              <div>
                <p class="comm_title" :class="commList[2].curr">
                  <strong>卡卡唯</strong>
                  <span class="comm_def" @click="likeGood(2)"><em>{{commList[2].num}}</em><img src="../assets/6_icon_good.png" /></span>
                  <span class="comm_active" @click="likeGood(2)"><em>{{commList[2].num}}</em><img src="../assets/6_icon_good2.png" /></span>
                </p>
                <p class="comm_content">谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工智能时代的创造造谷歌官方出品超轻量人工。</p>
                <p class="comm_time">4小时前</p>
              </div>
            </li>
          </ul>
        </div>
      </template>
      <el-comment @showComment="showComment" @hideComment="hideComment"></el-comment>
    </div>
    <div class="neterr" v-else>
        <img src="../assets/57_no_wifi.png" />
        <p class="net_msg">加载失败</p>
        <p class="net_reload" @click="reLoad">点击重新加载</p>
    </div>
  </div>
</template>
<script>
import Comment from "@/components/Comment";
export default {
  name: "detail",
  data() {
    return {
      sub: "sub_btn",
      comment: true,
      commList: [
        { curr: "on", num: 122 },//第一条评论已点赞
        { curr: "def", num: 122 },
        { curr: "def", num: 122 }
      ],
      comments: 2,
      network: false,
      backurl:'home'
    };
  },
  mounted(){
    this.backurl = this.$route.query.backurl;
  },
  methods: {
    backMine() {
      this.$router.push(this.backurl);
    },
    subscribe() {
      this.sub = "sub_onbtn";//点击订阅按钮后，按钮样式改变
    },
    likeGood(index) {
      if (this.commList[index].curr == "on") {
        this.commList[index].curr = "def";
        this.commList[index].num -= 1;
      } else {
        this.commList[index].curr = "on";
        this.commList[index].num += 1;
      }
    },
    showComment() {
      this.comment = false;
    },
    hideComment() {
      this.comment = true;
    },
    reLoad() {
      this.network = true;
    }
  },
  components: {
    "el-comment": Comment
  }
};
</script>
