<template>
  <div>
    <ul class="books">
      <li :key="item.name" v-for="item in books">
        <a :href="item.url" target="_blank">{{item.name}}</a>
      </li>
    </ul>
    <el-pagination
      background
      layout="total, prev, pager, next"
      :page-size="pageSize"
      :total="booksCount"
      :current-page="curPage" 
      prev-text="上一页" 
      next-text="下一页" 
      @current-change="currentChange"
    ></el-pagination>
  </div>
</template>
<script>
import booksObj from "../assets/book-urls";
export default {
  props: {
    type: {
      type: String,
      default: "frontend"
    }
  },
  data() {
    return {
      pageSize: 10,
      curPage: 1
    };
  },
  watch: {
    type(old, cur) {
      if (old !== cur) {
        this.curPage = 1;
      }
    }
  },
  computed: {
    books() {
      const _books = booksObj[this.type];
      let _curBooks = [];
      for (
        let index = (this.curPage - 1) * this.pageSize;
        index < _books.length && index < this.curPage - 1 + this.pageSize;
        index++
      ) {
        const _book = _books[index];
        _curBooks.push(_book);
      }
      return _curBooks;
    },
    booksCount() {
      return booksObj[this.type].length;
    }
  },
  methods: {
    currentChange(current) {
      this.curPage = current;
    }
  }
};
</script>
<style>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 10px 10px;
}
a {
  color: #42b983;
}
/* .books {
    height: 330px; 
} */
</style>

