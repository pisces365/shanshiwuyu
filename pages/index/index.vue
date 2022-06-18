<template>
	<view class="content">
		<scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower"@scroll="scroll">
			<view class="topimg" style="position: relative;">
				<image class="topbackgroud" mode="widthFix" src="https://s4.ax1x.com/2022/02/16/HhH9de.png"></image>
			</view>
			
			<view class="main">
				<view class="topbar">
					<view class="icon">
						<image class="imgicon" mode="heightFix" src="https://s4.ax1x.com/2022/02/16/HhHpZD.png"></image>
					</view>
					<view class="search">
						
					</view>
				</view>
				<view class="yijianshipu">
					<view class="center">
						<image style="display: block;margin: 0 auto;position: relative;" class="yijianshipuicon" mode="widthFix" src="https://s4.ax1x.com/2022/02/16/HhqJVU.png">
						</image>
					</view>
					<view style="font-size: 60rpx; text-align: center;">一键食谱</view>
				</view>
				<view style="height: 60rpx;"></view>
				<view class="belowbutton" style="display: flex;">
					<view class="fuyaotixing" style="flex: 1;" @click="navtofuyaotixing()">
						<image style="display: block;margin: 0 auto; width: 200rpx; padding: 50rpx 0rpx;" mode="widthFix" src="https://s4.ax1x.com/2022/02/16/HhTAkd.png">
						</image>
						<view style="font-size: 50rpx; text-align: center;">服药提醒</view>
					</view>
					<view class="yuyinzhushou" style="flex: 1;">
						<image style="display: block;margin: 0 auto; width: 200rpx; padding: 72rpx 0rpx;" mode="widthFix" src="https://s4.ax1x.com/2022/02/16/HhTFTH.png">
						</image>
						<view style="font-size: 50rpx; text-align: center;">智能语音助手</view>
					</view>
				</view>
			</view>
			<view style="height: 100rpx;"></view>
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		onLoad() {

		},
		methods: {
			navtofuyaotixing() {
				uni.navigateTo({
					url: "../fuyaotixing/fuyaotixing"
				})
			},
			
		}
	}
</script>

<style>
	.topbackgroud {
		width: 100%;
	}
	.imgicon {
		height: 70rpx;
	}
	.yijianshipuicon {
		padding: 120rpx 0;
		width: 260rpx;
	}
	.center {
		height: 510rpx;
		background-image: url(https://s4.ax1x.com/2022/02/16/HhTEtA.png);
		background-position: center 0;
		background-repeat: no-repeat;
		background-size: 500rpx;
	}
	.fuyaotixing {
		height: 300rpx;
		background-image: url(https://s4.ax1x.com/2022/02/16/HhT8ts.png);
		background-position: center 0;
		background-repeat: no-repeat;
		background-size: 300rpx;
	}
	.yuyinzhushou {
		height: 300rpx;
		background-image: url(https://s4.ax1x.com/2022/02/16/HhT8ts.png);
		background-position: center 0;
		background-repeat: no-repeat;
		background-size: 300rpx;
	}
</style>
