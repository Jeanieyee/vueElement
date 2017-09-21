<template>
  <div class="paginationBox">
    <ul :pagination="pagination">
      <li class="index" :class="{disabled: currentPage === 1}" @click="clickHandler(1)">首页</li>
      <li class="prev" :class="{disabled: currentPage === 1}" @click="clickHandler(currentPage - 1)">上一页</li>

      <li v-for="n in frontPage" :class="{cur: currentPage === n}" @click="clickHandler(n)">{{n}}</li>

      <li class="more">...</li>

      <li v-for="n in morePage" :class="{cur: currentPage === n, active: morePage === 0}" v-if="morePage > 0 && n > morePage - 5" @click="clickHandler(n)">{{n}}</li>

      <li class="more" v-if="morePage > 0">...</li>

      <li v-for="n in lastPage" :class="{cur: currentPage === n}" v-if="n >= lastPageStart" @click="clickHandler(n)">{{n}}</li>

      <li class="next" :class="{disabled: currentPage === totalPage}" @click="clickHandler(currentPage + 1)">下一页</li>
      <li class="last" :class="{disabled: currentPage === totalPage}" @click="clickHandler(totalPage)">尾页</li>
    </ul>
  </div>
</template>
<script>
  export default {
    name: 'pagination',
    props: ['pagination'],
    data () {
      return {
        pageSize: 5,
        frontPage: 5,
        morePage: 0,
        lastPageStart: this.pagination.totalPage,
        lastPage: this.pagination.totalPage,
        totalPage: this.pagination.totalPage,
        currentPage: 1
      }
    },
    methods: {
      clickHandler (currentPage) {
        if (currentPage > 0 && currentPage <= this.totalPage) {
          this.currentPage = currentPage
          if (this.currentPage >= this.pageSize) {
            this.frontPage = 1
            this.morePage = this.currentPage + 2
          } else {
            this.frontPage = this.pageSize
            this.morePage = 0
            this.lastPageStart = this.pagination.totalPage
          }
          if (this.currentPage > this.totalPage - this.pageSize + 1) {
            this.frontPage = 1
            this.morePage = 0
            this.lastPageStart = this.totalPage - this.pageSize + 1
          } else if (this.currentPage >= this.pageSize) {
            this.morePage = this.currentPage + 2
            this.lastPageStart = this.pagination.totalPage
          }
        }
      }
    }
  }
</script>
<style lang="scss">
  .paginationBox{
    ul{
      display: flex;
      display: -webkit-flex;
      flex-direction: row;
      justify-content: center;
      align-items: center;
      .prev,.index,.next,.last{
        padding:0 10px;
        width:auto;
      }
      .more{
        border:none;
      }
      .disabled{
        background: #ccc;
      }
      .cur{
        border:none;
        background: #42b983;
        color: #fff;
      }
      li{
        margin:0 10px;
        border:1px solid #ddd;
        width: 50px;
        height:50px;
        font-size:14px;
        text-align: center;
        line-height: 50px;
        cursor: default;
      }
    }
  }
</style>
