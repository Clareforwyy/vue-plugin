# vue-plugin

# 轮播
## vue-awesome-swiper  vue版swiper
- 安装
cnpm i vue-awesome-swiper --save
````
<template>
	<div class='slidefull'>
		<swiper :options='swiperOption' ref='mySwiper' >
		    <swiper-slide v-for='(item,index) in imgs'><div class='box' :key='index'>I'm Slide {{index}} <img :src='item.image_url' alt='' ></div></swiper-slide>
	  	</swiper>
	</div>
</template>
<script>
//引入swiper
import 'swiper/dist/css/swiper.css'
import { swiper, swiperSlide } from 'vue-awesome-swiper'
  export default {
    data() {
    	return {
	//以下配置可以去(swiper官网)看api[链接http://www.swiper.com.cn/api/]
	      	swiperOption: {
	          	direction: 'vertical',
		        slidesPerView: 1,
		        autoplay:true,
		        mousewheel: true,
		        loop:true,
		        pagination: {
		          el: '.swiper-pagination',
		          clickable: true,
		        }
	        },
	        imgs:[]
	      }
	},
    created(){
    	this.$ajax.get(this.$HttpConfig.LUNBOURL)
			.then((response)=>{
			    this.imgs = response.data.data;
			    console.log(this.imgs)
		  	})
		  	.catch((error)=>{
		    	console.log(error);
		  	})
    },
    components: {
	    swiper,
	    swiperSlide
	  }
  }
</script>
<style>
	.swiper-container{
		height: 100%;
	}
</style>
<style scoped lang='less'>
.slidefull{
	height: 100%;
	.box{
		background: green;
		height: 100%;
		img{
			height: 100%;
			width: 100%;
		}
	}
}
</style>
````
