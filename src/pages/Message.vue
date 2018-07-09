<template>
    <div class="msg_wrap">
        <div class="msg_header">
          <h2>消息通知</h2>
          <img src="../assets/back.png" alt="" @click="backMine" class="default_back">
          <img src="../assets/dark_back.png" alt="" @click="backMine" class="dark_back">
        </div>
        <ul class="msg_list">
          <li>
            <img src="../assets/girl.png" alt="">
            <div>
              <h3>
                <strong>蓝小穹</strong>
                <span>11-20</span>
              </h3>
              <p>欢迎使用蓝穹APP阅读时事金融新闻，一手掌握最新金融资讯尽在蓝穹APP！</p>
            </div>
          </li>
          <li>
            <img src="../assets/girl.png" alt="">
            <div>
              <h3>
                <strong>蓝小穹</strong>
                <span>11-18</span>
              </h3>
              <p>蓝穹APP已经陪伴你1325天了，感谢有你在的日子，今后将陪伴你走过更多的日子哦。</p>
            </div>
          </li>
        </ul>
        <el-nav index="3"></el-nav>   <!--父组件为当前组件，子组件为nav导航，根据index的值来切换导航图标-->
    </div>
</template>

<script>
import Nav from "@/components/Navgiator";
export default {
  data() {
    return {};
  },
  components: {
    "el-nav": Nav
  },
  methods: {
    backMine() {
      this.$router.push("my");
    }
  }
};
</script>
