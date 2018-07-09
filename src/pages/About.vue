<template>
    <div class="about_wrap">
        <div class="msg_header">
          <h2>关于蓝穹</h2>
          <img src="../assets/back.png" alt="" @click="backMine" class="default_back">
          <img src="../assets/dark_back.png" alt="" @click="backMine" class="dark_back">
        </div>
        <div class="about">
          <p>蓝穹新闻订阅APP是一款新闻定向推送及订阅类的APP。</p>
          <p style="text-indent:2em;">2016年12月1日，中国保监会发文批准招商局仁和人寿保险股份有限公司筹建。注册资本人民币50亿元，注册地深圳市。拟任董事长李建红，拟任总经理彭伟。</p>
          <h3>招商局仁和人寿保险股份有限公司筹备组：</h3>
          <p>你筹备组关于筹建招商局仁和人寿保险股份有限公司的申请及相关补正材料收悉。经研究，现批复如下：</p>
          <ul class="txt">
            <li>一、同意深圳市招融投资控股有限公司、中国移动通信集团公司、中国民航信息网络股份有限公司、深圳市投资控股有限公司、深圳市卓越创业投资有限责任公司、深圳光汇石油集团股份有限公司、深圳市前海金融控股有限公司、亿赞普（北京）科技有限公司等8家公司共同发起筹建招商局仁和人寿保险股份有限公司，注册资本人民币50亿元，注册地深圳市。拟任董事长李建红，拟任总经理彭伟。</li>
            <li>二、你筹备组应当自收到批准筹建通知之日起1年内完成筹建工作，筹建期间不得从事保险经营活动，未经批准不得变更投资人、拟任董事长和拟任总经理。</li>
            <li>三、你筹备组应当严格依照有关法律法规办理筹建事宜，并将筹建过程中的有关情况及时报告我会。</li>
            <li>四、筹建完毕，你筹备组应当及时上报开业申请。在我会验收合格并下达开业批复后，再到工商部门注册登记。</li>
          </ul>
          <ul class="picture">
            <li>
              <div><img src="../assets/29_img.png" alt=""></div>
              <h4>照片1</h4>
              <p>招商局仁和人寿保险股份有限公司</p>
            </li>
            <li>
              <div><img src="../assets/30_img.png" alt=""></div>
              <h4>照片2</h4>
              <p>招商局仁和人寿保险股份有限公司</p>
            </li>
            <li>
              <div><img src="../assets/31_img.png" alt=""></div>
              <h4>照片3</h4>
              <p>招商局仁和人寿保险股份有限公司</p>
            </li>
            <li>
              <div><img src="../assets/32_img.png" alt=""></div>
              <h4>照片4</h4>
              <p>招商局仁和人寿保险股份有限公司</p>
            </li>
          </ul>
        </div>
        <div class="address">
          <ul>
            <li>
              <h3>联系我们</h3>
              <p>236687</p>
            </li>
            <li>
              <h3>更多联系方式</h3>
            </li>
            <li>
              <h3>关于公司</h3>
              <p>工作机会</p>
              <p>法律声明</p>
              <p>企业责任</p>
              <p>网站地图</p>
            </li>
            <li>
              <h3>关注我们</h3>
              <p>
                <img src="../assets/wechat.png" alt="">
                <img src="../assets/sina.png" alt="">
              </p>
            </li>
          </ul>
        </div>
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
