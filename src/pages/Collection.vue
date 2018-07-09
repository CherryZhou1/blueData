<template>
  <div class="collection_wrap" :style="opt == 2 ?styleobj:''">
    <div class="coll_header">
      <img src="../assets/back.png" alt="" @click="backMine" class="default_back">
      <img src="../assets/dark_back.png" alt="" @click="backMine" class="dark_back">
      <ul>
        <li :class="curtab==1 ?'on':''" @click="changeTab(1)">收藏</li>
        <li @click="changeTab(2)" :class="curtab==2 ?'on':''">历史</li>
      </ul>
      <p @click="editOpt">{{opt == 1 ? '编辑':'取消'}}</p>
    </div>
    <template v-if="curtab==1">
      <ul class="coll_list">
        <li v-for="(item, index) in colls" :key="index">
          <p class="coll_select" v-if="opt == 2"><input type="checkbox" :value="index" v-model="selected" :id="'myCheck'+index"><label :for="'myCheck'+index"></label></p>
          <div class="coll_txt">
            <h3>{{item.title}}</h3>
            <p>{{item.time}}<span>{{item.author}}</span></p>
          </div>
          <p class="coll_img"><img src="../assets/img_200X150.png" alt="" ></p>
        </li>
      </ul>
      <p class="coll_all">{{showAll}}</p>
      <div class="coll_opt" v-if="opt == 2">
        <span><label for="selectall">全选</label><input type="checkbox" id="selectall" class="checkbox" @click="selectAllColl" /></span>
        <span @click="delColl">删除</span>
      </div>
    </template>
    <template v-else>
      <ul class="coll_list">
        <li v-for="(item, index) in history" :key="index">
          <p class="coll_select" v-if="opt == 2"><input type="checkbox" :value="index" v-model="selectedH" :id="'history'+index"><label :for="'history'+index"></label></p>
          <div class="coll_txt">
            <h3>{{item.title}}</h3>
            <p>{{item.time}}<span>{{item.author}}</span></p>
          </div>
          <p class="coll_img"><img src="../assets/img_200X150.png" alt="" ></p>
        </li>
      </ul>
      <p class="coll_all">{{showAllH}}</p>
      <div class="coll_opt" v-if="opt == 2">
        <span><label for="hselectall">全选</label><input type="checkbox" id="hselectall" class="checkbox" @click="selectAllH" /></span>
        <span @click="delH">删除</span>
      </div>
    </template>
  </div>
</template>
<script>
export default {
  data() {
    return {
      colls: [
        {
          title: "谷歌官方出品：超轻量人工智能时代的创造创造...",
          author: "UC新闻1",
          time: "2017-10-11"
        },
        {
          title: "谷歌官方出品：超轻量人工智能时代的创造创造...",
          author: "UC新闻2",
          time: "2017-10-11"
        },
        {
          title: "谷歌官方出品：超轻量人工智能时代的创造创造...",
          author: "UC新闻3",
          time: "2017-10-11"
        }
      ],
      selected: [],
      selectedH: [],
      showAll: "已显示全部内容",
      showAllH: "已显示全部内容",
      curtab: 1,
      history: [
        {
          title: "2谷歌官方出品：超轻量人工智能时代的创造创造...",
          author: "UC新闻1",
          time: "2017-10-11"
        },
        {
          title: "2谷歌官方出品：超轻量人工智能时代的创造创造...",
          author: "UC新闻2",
          time: "2017-10-11"
        },
        {
          title: "2谷歌官方出品：超轻量人工智能时代的创造创造...",
          author: "UC新闻3",
          time: "2017-10-11"
        }
      ],
      opt: 1,
      styleobj: {
        paddingBottom: ".9rem"
      }
    };
  },
  methods: {
    backMine() {
      this.$router.push("my");
    },
    selectAllColl(event) {
      var _this = this;
      if (!event.currentTarget.checked) {
        this.selected = [];
      } else {
        //实现全选
        _this.selected = [];
        _this.colls.forEach(function(item, i) {
          _this.selected.push(i);
        });
      }
    },
    delColl() {
      let arr = [];
      var len = this.colls.length;
      for (var i = 0; i < len; i++) {
        if (this.selected.indexOf(i) >= 0) {
        } else {
          arr.push(this.colls[i]);
        }
      }
      this.colls = arr;
      this.selected = [];
      this.showAll = "没有内容了哦";
    },
    changeTab(index) {
      this.curtab = index;
    },
    selectAllH(event) {
      var _this = this;
      if (!event.currentTarget.checked) {
        this.selectedH = [];
      } else {
        //实现全选
        _this.selectedH = [];
        _this.history.forEach(function(item, i) {
          _this.selectedH.push(i);
        });
      }
    },
    delH() {
      let arr = [];
      var len = this.history.length;
      for (var i = 0; i < len; i++) {
        if (this.selectedH.indexOf(i) >= 0) {
        } else {
          arr.push(this.history[i]);
        }
      }
      this.history = arr;
      this.selectedH = [];
      this.showAllH = "没有内容了哦";
    },
    editOpt() {
      if (this.opt == 1) {
        this.opt = 2;
      } else {
        this.opt = 1;
      }
    }
  }
};
</script>