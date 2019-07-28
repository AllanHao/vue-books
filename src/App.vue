<template>
  <div id="app">
    <el-menu default-active="frontend" mode="horizontal" @select="handleSelect">
      <el-menu-item index="frontend">前端</el-menu-item>
      <el-menu-item index="backend">后端</el-menu-item>
      <el-menu-item index="sql">数据库</el-menu-item>
      <el-menu-item index="dataStructure">数据结构与算法</el-menu-item>
    </el-menu>
    <!-- <router-view />
    <ul>
      <li :key="item.name" v-for="item in book">
        <a :href="item.url" target="_blank">{{item.name}}</a>
      </li>
    </ul> -->
    <book-page :type="type"></book-page>
  </div>
</template>

<script>
import BookPage from "./components/BookPage";
export default {
  name: "App",
  components: {BookPage},
  data() {
    return {
      type: "frontend"
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      this.type = key;
      // this.$router.push({ name: 'books', params: { type: key } })
      console.log(key, keyPath);
    }
  },
  mounted() {}
};
</script>

<style>
body,
html {
  margin: 0;
  padding: 0;
  height: 100%;
}
h1,
h2 {
  font-weight: normal;
}
</style>
