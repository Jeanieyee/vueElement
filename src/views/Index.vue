<template>
  <div class="containtBox">
    <h3>tab切换：</h3>
    <tab-change tabsNumber=4>
      <template slot="tab-0">tab-0</template>
      <template slot="tab-1">tab-1</template>
      <template slot="tab-2">tab-2</template>
      <template slot="tab-3">tab-3</template>
      <template slot="tabs-0">tabs-0-content</template>
      <template slot="tabs-1">tabs-1-content</template>
      <template slot="tabs-2">tabs-2-content</template>
      <template slot="tabs-3">tabs-3-content</template>
    </tab-change>
  </div>
</template>
<script>
  import TabChange from '../components/TabChange.vue'
  export default {
    name: 'index',
    components: {
      TabChange
    }
  }
</script>
<style lang="scss">
  h3{
    margin:0 auto !important;
    width: 500px;
    text-align: left;
    font-size: 20px;
    line-height: 100px;
  }
  .tabChangeBox{
    margin:0 auto;
    border:1px solid #ddd;
    width:400px;
    ul{
      border-bottom:1px solid #ddd;
      display: flex;
      display: -webkit-flex;
      flex-direction: row;
      justify-content: space-between;
      li{
        width:100px;
        height:60px;
        font-size:16px;
        line-height: 60px;
        text-align: center;
        cursor: default;
      }
      .active{
        color: #42b983;
      }
    }
    .tabs{
      padding: 30px;
    }
  }
</style>
