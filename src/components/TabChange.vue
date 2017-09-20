<template>
  <div class="tabChangeBox">
      <ul :tabsNumber="tabsNumber">
        <li v-for="(item, index) in activeTabs" :class="{active: activeTabs[index]}" @click="tabChange(index)">
          <slot :name="`tab-${index}`"></slot>
        </li>
      </ul>
      <div class="tabs" v-for="(item, index) in activeTabs" v-show="activeTabs[index]">
        <slot :name="`tabs-${index}`"></slot>
      </div>
  </div>
</template>
<script>
  export default {
    name: 'tabChange',
    props: ['tabsNumber'],
    data () {
      let activeTabs = []
      for (let i = 0; i < this.tabsNumber; i++) {
        if (i === 0) activeTabs.push(true)
        else activeTabs.push(false)
      }
      return {
        activeTabs: activeTabs
      }
    },
    methods: {
      tabChange (index) {
        this.activeTabs.forEach((item, i) => {
          this.$set(this.activeTabs, i, false)
        })
        this.$set(this.activeTabs, index, true)
      }
    }
  }
</script>
