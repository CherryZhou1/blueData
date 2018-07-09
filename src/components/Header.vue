<template>
<div class="header">
    <p>{{title}}</p>
    <img src="../assets/search.png" @click="search" class="default_search" />
    <img src="../assets/40_dark_search.png" @click="search" class="dark_search" />
</div>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    title: String
  },
  methods: {
    search() {
      this.$router.push("search");
    }
  }
};
</script>