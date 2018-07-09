<template>
    <div class="mine_wrap">
        <h2>我的</h2>
        <div class="mine">
            <div class="avater">
                <p><img src="../assets/avater.png" /></p>
            </div>
            <router-link to="/coll" class="collection">
                <p><img src="../assets/collection.png" /></p>
                <p>收藏与历史</p>
            </router-link>
            <ul class="notice">
                <li class="new">
                    <router-link to="/msg">
                        <p>消息通知</p>
                        <img src="../assets/dark_back.png" />
                    </router-link>
                </li>
                <li>
                    <div>
                        <p>{{theme}}</p>
                        <strong @click="switchDark" :class="dark?'':'swright'"><i></i></strong>
                    </div>
                </li>
            </ul>
            <ul class="notice">
                <li>
                    <router-link to="/about">
                        <p>关于</p>
                        <img src="../assets/dark_back.png" />
                    </router-link>
                </li>
                <li>
                    <router-link to="/like">
                        <p>赞过的</p>
                        <img src="../assets/dark_back.png" />
                    </router-link>
                </li>
                <li class="new">
                    <router-link to="">
                        <p>当前版本</p>
                        <span>1.0</span>
                    </router-link>
                </li>
            </ul>
        </div>
        <el-nav index="3"></el-nav>
    </div>
</template>

<script>
import Nav from "@/components/Navgiator";
export default {
  data() {
    return {
      dark:false,
      theme:"夜间模式"
    };
  },
  components: {
    "el-nav": Nav
  },
  methods:{
    switchDark(){
      this.dark = !this.dark;
      if(this.dark){
        document.getElementsByTagName("body")[0].className="dark";
        this.theme="日间模式"
      }else{
        document.getElementsByTagName("body")[0].className="";
      }
    }
  }
};
</script>
