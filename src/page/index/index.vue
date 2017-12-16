<template>
  <div>
  	<header class="header">
  		<div class="back iconfont">&#xe624;</div>
  		<div class="search"><a href="#" class="prompt">请输入城市/景点/游戏主题</a></div>
  		<div class="city">城市</div>
  	</header>
  	 <swiper :options="swiperOption">
      <swiper-slide>
        <div class="swiper-img-con">
          <img  class="swiper-img" src="http://img1.qunarzz.com/piao/fusion/1609/15/630b82d932a3c402.jpg_640x200_862e836b.jpg"/>
        </div>
      </swiper-slide>
      <swiper-slide>
        <div class="swiper-img-con">
          <img class="swiper-img" src="http://img1.qunarzz.com/piao/fusion/1712/5c/723bbb93e9683f02.jpg_640x200_7d38c6ad.jpg"/>
        </div>
      </swiper-slide>
      <div class="swiper-pagination"  slot="pagination"></div>
    </swiper>

  </div>
</template>

<script>
export default {
  name: 'Index',
  data () {
    return {
      swiperOption: {
        autoplay: 1000,
        direction: 'horizontal'
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
		/*position: relative;*/
		text-overflow: ellipsis;
		white-space: nowrap;
		
	}
	.swiper-img-con{
		width: 100%;
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
</style>