<template>
	<view>
		<view class="uni-padding-wrap">
			<view class="page-section swiper">
				<view class="page-section-spacing">
					<swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration">
						<swiper-item v-for="(item,index) in swipers" :key="index">
								<image :src="item.img"></image>
						</swiper-item>
					</swiper>
				</view>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				swipers:[]	,
				indicatorDots: true,
				autoplay: true,
				interval: 2000,
				duration: 500
			}
		},
		onLoad() {
			this.getSwipers()
		},
		methods: {
		//获取轮播图的数据
			async getSwipers(){
				console.log('获取轮播图的数据')
				// uni.request({
				// 	url:'http://localhost:8082/api/getlunbo',
				// 	success:(res)=> {
				// 		console.log(res)
				// 		if(res.data.status !==0){
				// 			return uni.showToast({
				// 				title:'获取数据失败'
				// 			})
				// 		}
				// 		this.swipers = res.data.message
				// 		console.log(this.swipers)
				// 	}
				// })
				const res = await this.$myRequest({
					url:'/api/getlunbo'
				})
				console.log(res)
				this.swipers = res.data.message
				console.log(this.swipers)
			}
		}
	}
</script>

<style lang="scss">
	.uni-padding-wrap{
		text-align: center;
		uni-image{
			width: 375px;
		} 
	}
	
</style>
