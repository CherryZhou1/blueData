<template>
    <div class="home_wrap">
        <el-header title="新闻"></el-header>
          <div class="news">
            <p v-if="refresh" class="refreshRes">更新了10条记录</p>
            <v-scroll :on-refresh="onRefresh" :on-infinite="onInfinite" :dataList="scrollData">
              <ul>
                  <li v-for="(item,index) in listdata" :key="index">
                    <!--item.showType == 1指置顶+右侧小图的新闻标题类型-->
                      <router-link :to="{ path: '/detail', query: { id: 1,backurl:'home'}}" v-if="item.showType == 1">
                          <div class="list">
                              <div class="list_info">
                                  <h2>{{item.title}}</h2>
                                  <div>
                                      <strong>置顶</strong>
                                      <span>{{item.time}}</span>
                                      <p class="scomment"><img src="../assets/comment.png" /><span>{{item.comment}}</span></p>
                                      <p><img src="../assets/good.png" /><span>{{item.star}}</span></p>
                                  </div>
                              </div>
                              <p class="pic"><img :src="item.img" /></p>
                          </div>
                      </router-link>
                    <!--item.showType == 2指下方大图的新闻标题类型-->
                      <router-link :to="{ path: '/detail', query: { id: 1,backurl:'home'}}" v-else-if="item.showType == 2">
                          <div class="list_pic">
                              <h2>{{item.title}}</h2>
                              <p class="pic"><img :src="item.img" /></p>
                              <div class="pic_info">
                                  <span>{{item.time}}</span>
                                  <p class="scomment"><img src="../assets/comment.png" /><span>{{item.comment}}</span></p>
                                  <p><img src="../assets/good.png" /><span>{{item.star}}</span></p>
                              </div>
                          </div>
                      </router-link>
                    <!--指不含图片的新闻标题类型-->
                      <router-link :to="{ path: '/detail', query: { id: 1,backurl:'home'}}" v-else>
                          <div class="list_pic txt">
                              <h2>{{item.title}}</h2>
                              <div class="pic_info">
                                  <span>{{item.time}}</span>
                                  <p class="scomment"><img src="../assets/comment.png" /><span>{{item.comment}}</span></p>
                                  <p><img src="../assets/good.png" /><span>{{item.star}}</span></p>
                              </div>
                          </div>
                      </router-link>
                  </li>
              </ul>
            </v-scroll>
          </div>
        <el-nav index="1"></el-nav>
    </div>
</template>

<script>
import Nav from "@/components/Navgiator";
import Header from "@/components/Header";
import Scroll from "@/components/Scroll";
export default {
  data() {
    return {
      counter: 1, //当前页
      num: 10, // 一页显示多少条
      pageStart: 0, // 开始页数
      pageEnd: 0, // 结束页数
      listdata: [], // 下拉更新数据存放数组
      scrollData: {
        noFlag: false //暂无更多数据显示
      },
      refresh: false
    };
  },
  components: {
    "el-nav": Nav,
    "el-header": Header,  //Header.vue组件
    "v-scroll": Scroll
  },
  created: function() {
    this.getList();
  },
  methods: {
    getList() {
      var response = [];
      for (let i = 0; i < 20; i++) {
        var showType = this.randomNum(1, 3);
        var img = "";
        if (showType == 1) {
          img = "static/images/img_200X150.png";
        } else if (showType == 2) {
          img = "static/images/img_690X270.png";
        } else {
          img = "";
        }
        response.push({
          title: "谷歌官方出品：超轻量一键清理软件小助理",
          time: "刚刚更新" + i,
          comment: "999+",
          star: "999+",
          img: img,
          showType: showType
        });
      }
      this.listdata = response.slice(0, this.num);//上面随机生成20条新闻，然后只显示10条
    },
    onRefresh(done) {
      this.getList();

      done(); // call done
      this.refresh = true;
      var self = this;
      //用一个变量保存当前函数执行环境中的this对象
      //这里可能会有疑问：为什么非得把this保存起来呢？这是因为，内部函数（比如本函数里面包含的两个匿名函数）
      //在搜索this变量时，只会搜索到属于它自己的this，而不会搜索到包含它的那个函数的this。
      //所以，为了在内部函数能使用外部函数的this对象，要给它赋值了一个名叫self的变量。
      setTimeout(function() {
        self.refresh = false;
      }, 2000);
    },
    onInfinite(done) {
      this.counter++;
      let end = (this.pageEnd = this.num * this.counter);
      let i = (this.pageStart = this.pageEnd - this.num);

      let more = this.$el.querySelector(".load-more");
      for (i; i < end; i++) {
        if (i >= 30) {
          more.style.display = "none"; //隐藏加载条
          //走完数据调用方法
          this.scrollData.noFlag = true;

          break;
        } else {
          var showType = this.randomNum(1, 3);
          var img = "";
          if (showType == 1) {
            img = "static/images/img_200X150.png";
          } else if (showType == 2) {
            img = "static/images/img_690X270.png";
          } else {
            img = "";
          }
          this.listdata.push({
            title: "谷歌官方出品：超轻量一键清理软件小助理",
            time: "刚刚更新" + i,
            comment: "999+",
            star: "999+",
            img: img,
            showType: showType
          });
          more.style.display = "none"; //隐藏加载条
        }
      }
      done();
    },
    randomNum(minNum, maxNum) {
      switch (arguments.length) {
        case 1:
          return parseInt(Math.random() * minNum + 1, 10);
          break;
        case 2:
          return parseInt(Math.random() * (maxNum - minNum + 1) + minNum, 10);
          break;
        default:
          return 0;
          break;
      }
    }
  }
};
</script>
