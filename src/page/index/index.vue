<template>
  <div>
  	<header class="header">
  		<div class="back iconfont">&#xe624;</div>
  		<div class="search"><a href="" title="" class="prompt">输入城市/景点/游玩主题</a></div>
  		<div class="city">城市</div>
  	</header>
  	 <swiper :options="swiperOption">
      <swiper-slide v-for="item in swiperInfo" :key="item.id">
        <div class="swiper-img-con">
          <img  class="swiper-img" :src="item.imgUrl"/>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>

    <swiper>
      <swiper-slide v-for="(pageInfo, index) in pages" :key="index">
        <div class="icon-wrapper">
          <div v-for="item in pageInfo" :key="item.id" class="icon-item">
            <div class="icon-img-con">
              <img  class="icon-img" :src="item.imgUrl"/>
            </div>
            <p class="size">{{item.msg}}</p>
          </div>
        </div>
      </swiper-slide>
    </swiper>
    <div class="swiper-pagination"  slot="pagination"></div>

    <div class="section-position">
      <div class="position-left">定位失败</div>
      <div class="position-right">5折泡温泉</div>
    </div>
    <div class="section-wenquan">
      <div class="wenquan-left" style="background:url(http://img1.qunarzz.com/piao/fusion/1710/a2/e395615b16fb1302.png) center center no-repeat;background-size:auto 100%;"></div>
      <div class="wenquan-right" style="background:url(http://img1.qunarzz.com/piao/fusion/1711/8a/4c62d1a89fc2d602.png) center center no-repeat;background-size:auto 100%;"></div>
    </div>

    <div class="her">热门推荐</div>

    <div class="hot">
      <ul>
        <li v-for="item in hots" class="hot-li">
            <div class="hot-img">
              <img :src="item.imgUrl" alt="" class="hot-img-size">
            </div>
            <div class="hot-right">
              <p class="right-name">{{item.name}}</p>
              <p class="right-msg">{{item.msg}}</p>
              <p class="right-price">{{item.sprice}}</p>
            </div>
        </li>
      </ul>
    </div>
    
    <div class="chakan">查看所有产品</div>

    <div class="her">周末去哪儿</div>

    <div class="week">
      <ul>
        <li v-for="item in week">
          <div class="week-img">
            <img :src="item.imgUrl" alt="" class="week-imgs">
          </div>
          <div class="week-bottom">
            <p class="bottom-name">{{item.name}}</p>
            <p class="bottom-msg">{{item.msg}}</p>
          </div>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      swiperInfo: [],
      iconInfo: [],
      hots: [],
      week: [],
      swiperOption: {
        autoplay: 1000,
        pagination: {
          el: '.swiper-pagination',
          loop: true
        }
      }
    }
  },
  computed: {
    pages () {
      const pages = []
      this.iconInfo.forEach((value, index) => {
        let page = Math.floor(index / 8)
        if (!pages[page]) {
          pages[page] = []
        }
        pages[page].push(value)
      })
      return pages
    }
  },
  created () {
    this.getIndexData()
  },
  methods: {
    getIndexData () {
      this.$http.get('/static/index.json')
      .then(this.handleGetDataSucc.bind(this))
    },
    handleGetDataSucc (res) {
      const body = res.body
      console.log(res)
      if (body && body.data && body.data.swiper && body.data.hot) {
        this.swiperInfo = res.body.data.swiper
        this.iconInfo = res.body.data.icons
        this.hots = res.body.data.hot
        this.week = res.body.data.week
        console.log(this.iconInfo)
        console.log(this.hots)
        console.log(this.week)
      }
    }
  }
}
</script>


<style scoped>
  .header{
    display: flex;
    height: 0.86rem;
    background: #05bad5;
    color: #FFFFFF;
  }

  .back{
    width: .64rem;
    line-height: 0.86rem;
    text-align: center;
  }
  .search{
    margin: .14rem .18rem;
    flex: 1;
    background: #FFFFFF;
    border-radius: 0.1rem ;
  }
  .city{
    width: 1.32rem;
    line-height: .86rem;
    text-align: left;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
  .swiper-img-con{
    overflow: hidden;
    width: 100%;
    height: 0;
    padding-bottom: 31.25%;
  }
  .swiper-img{
    width: 100%;
  }
  .prompt{
    text-align: center;
    display: block;
    line-height: 0.6rem;
    height: 0.6rem;
  }
  .city:after{
    display:block;
    content:'';
    border-width:0.13rem;
    border-style:solid;
    border-color:#FFFFFF transparent transparent transparent;
    position:absolute;
    top: 0.35rem;
    right: 0.3rem;
}
  .icon-wrapper {
  }
  .icon-item {
    box-sizing: border-box;
    float: left;
    width: 25%;
    padding: .4rem;
  }
  .icon-img-con {
    width: 100%;
    height: 0;
    padding-bottom: 60%;
  }
  .icon-img {
    width: 60%;
    display: block;
    margin: 0 auto;
  }
  .size {
    font-size: 0.30rem;
    text-align: center;
    margin-top: 0.2rem;
  }
  .section-position{
    height: .96rem;
    display: flex;
    justify-content: space-between;
  }
  .position-left,.position-right{
    flex: 1;
    text-align: center;
    line-height: 0.96rem;
    border: 1px solid #eee;
  }
  .section-wenquan{
    height: 1.4rem;
    display: flex;
    justify-content: space-between;
    margin-top: 0.3rem;
  }
  .wenquan-left,.wenquan-right{
    flex: 1;
    text-align: center;
    line-height: 0.96rem;
    border: 1px solid #eee;
  }
  .her{
    height: 0.8rem;
    line-height: 0.8rem;
    padding-left: 0.26rem;
    background: #f5f5f5;
  }
  .hot-li{
    height: 1.4rem;
    padding: .24rem;
    display: flex;
  }
  .hot-img{
    display: inline-block;
    width: 1.4rem;
    height: 1.4rem;
  }
  .hot-img-size{
    width: 100%;
  }
  .hot-right{
    margin-left: .1rem;
  }
  .right-name{
    margin-bottom: .2rem;
  }
  .right-msg{
    margin-bottom: .2rem;
    color: #9e9e9e;
  }
  .right-price{
    color: #ff8300;
    font-size: .46rem;
  }
  .chakan{
    height: .88rem;
    line-height: .88rem;
    text-align: center;
    color: #00afc7;
  }
  .week-img{
    height: 3.18rem;
  }
  .week-imgs{
    width: 100%;
  }
  .week-bottom{
    height: 1.2rem;
    padding: .14rem .2rem .2rem .2rem;
  }
  .bottom-name{
    font-size: .36rem;
    line-height: .48rem;
  }
  .bottom-msg{
    font-size: .28rem;
    color: #616161;
    margin-top: .2rem;  
  }
</style>