<template>
</template>
<script>
export default {name: 'Index',data () {return {swiperOption: {autoplay: 1000,direction: 'horizontal',pagination: {el: '.swiper-pagination'}}}},created () {this.getIndexData()},methods: {getIndexData () {this.$http.get('/static/index.json').then(this.handleGetDataSucc.bind(this))},handleGetDataSucc (res) {console.log(res)}}}
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
</style>