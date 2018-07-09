<template>
    <div class="search">
        <div class="search_key">
            <div>
                <input type="text" placeholder="请输入关键字" v-model="stxt" />
                <img src="../assets/delete.png" @click="delSearch" v-if="stxt" class="dark_del" />
                <img src="../assets/44_delete.png" @click="delSearch" v-if="stxt" class="default_del" />
            </div>
            <p @click="backPage">取消</p>
        </div>
       
        <template v-if="isSearch">
          <div class="search_res" v-if="haveData">
            <div class="list">
                <div class="list_info">
                    <h2>谷歌官方出品：超轻量人工智能时代的创造</h2>
                    <div>
                        <strong>置顶</strong>
                        <span>刚刚更新</span>
                        <p class="scomment"><img src="../assets/comment.png" /><span>999+</span></p>
                        <p><img src="../assets/good.png" /><span>999+</span></p>
                    </div>
                </div>
                <img src="../assets/img_200X150.png" class="pic" />
            </div>
            <div class="list">
                <div class="list_info">
                    <h2>谷歌官方出品：超轻量人工智能时代的创造</h2>
                    <div>
                        <span>刚刚更新</span>
                        <p class="scomment"><img src="../assets/comment.png" /><span>999+</span></p>
                        <p><img src="../assets/good.png" /><span>999+</span></p>
                    </div>
                </div>
                <img src="../assets/img_200X150.png" class="pic" />
            </div>
            <div class="list_pic">
                <h2>谷歌官方出品：超轻量一键清理软件小助理</h2>
                <img src="../assets/img_690X270.png" class="pic" />
                <div class="pic_info">
                    <span>刚刚更新</span>
                    <p class="scomment"><img src="../assets/comment.png" /><span>999+</span></p>
                    <p><img src="../assets/good.png" /><span>999+</span></p>
                </div>
            </div>
            <div class="list_pic txt">
                <h2>谷歌官方出品：超轻量一键清理软件小助理</h2>
                <div class="pic_info">
                    <span>刚刚更新</span>
                    <p class="scomment"><img src="../assets/comment.png" /><span>999+</span></p>
                    <p><img src="../assets/good.png" /><span>999+</span></p>
                </div>
            </div>
            <p class="endtips">已显示全部内容</p>
          </div>
          <div class="search_no" v-else>
            <div>
                <img src="../assets/load_fail.png" />
                <p>无相关关键词文章</p>
            </div>
          </div>
        </template>
        <div class="hot_key" v-else>
            <h2>热门搜索关键字</h2>   
            <ul>
                <li>招商仁和</li>
                <li>科技时事</li>
                <li>十二纪念日</li>
                <li>深圳时事</li>
                <li>设计资讯</li>
            </ul>     
        </div>
    </div>
</template>

<script>
export default {
  data() {
    return {
      isSearch: false,
      stxt: null,
      haveData: true
    };
  },
  methods: {
    delSearch() {
      this.stxt = null;
    },
    // 目前还不知道搜索按钮在什么地方
    startSearch() {
      this.isSearch = !this.isSearch;
      if (!this.isSearch) {
        this.stxt = null;
      }
    },
    backPage() {
      this.$router.push("home");
    }
  }
};
</script>