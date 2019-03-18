<template>
  <div>
    <x-header :right-options="{showMore: true}" :left-options="{showBack: false}">我爱阅读</x-header>
    <swiper loop auto :list="demo06_list" :index="demo06_index"></swiper>
        <grid :show-lr-borders="false">
      <grid-item :label="('Grid')" v-for="i in 4" :key="i">
        <img slot="icon" src="../assets/grid_icon.png">
      </grid-item>
    </grid>
    <tabbar>
      <tabbar-item>
        <img slot="icon" src="../assets/home.png">
        <span slot="label">首页</span>
      </tabbar-item>
      <tabbar-item show-dot>
        <img slot="icon" src="../assets/book.png">
        <span slot="label">阅读</span>
      </tabbar-item>
      <tabbar-item selected>
        <img slot="icon" src="../assets/map.png">
        <span slot="label">附近</span>
      </tabbar-item>
      <tabbar-item badge="2">
        <img slot="icon" src="../assets/mine.png">
        <span slot="label">我的</span>
      </tabbar-item>
    </tabbar>
  </div>
</template>

<script>
import { Tabbar, TabbarItem, Group, Cell, XHeader, Swiper, Grid, GridItem } from 'vux'

const baseList = [{
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vvsr72j20p00gogo2.jpg',
  title: '送你一朵fua'
}, {
  url: 'javascript:',
  img: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw1k2wj20p00goq7n.jpg',
  title: '送你一辆车'
}, {
  url: 'javascript:',
  img: 'https://static.vux.li/demo/5.jpg', // 404
  title: '送你一次旅行',
  fallbackImg: 'https://ww1.sinaimg.cn/large/663d3650gy1fq66vw50iwj20ff0aaaci.jpg'
}]

const urlList = baseList.map((item, index) => ({
  url: 'http://m.baidu.com',
  img: item.img,
  fallbackImg: item.fallbackImg,
  title: `(可点击)${item.title}`
}))

export default {
  components: {
    Grid,
    GridItem,
    Swiper,
    XHeader,
    Tabbar,
    TabbarItem,
    Group,
    Cell
  },
  methods: {
    login () {
      this.$router.push({ path: 'Login'})
    }
  },
  created () {
    let _this = this
    this.$http.post('https://api.apiopen.top/getJoke').then(({data}) => {
      console.log(data)
      var new_data = data.result.map((item, index) => ({
        src: item.header,
        fallbackSrc: item.header,
        title: item.name,
        desc: item.text
      }))
      console.log(new_data)
      _this.list = new_data
    })
  },

  data () {
    return {
      demo06_list: urlList,
      demo06_index: 0
    }
  }
}
</script>