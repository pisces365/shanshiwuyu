<template>
	<view class="content">
		<scroll-view :scroll-top="scrollTop" scroll-y="true" class="" @scrolltoupper="upper" @scrolltolower="lower"@scroll="scroll">
			<view class="topimg" style="position: relative;">
				<image class="topbackgroud" mode="widthFix" src="https://s4.ax1x.com/2022/02/16/HhH9de.png"></image>
				<view class="back" style="position: absolute; left: 20rpx; bottom: 20%;" @click="navback()"></view>
			</view>
			<view class="main">
				<view class="topbar">
					<view class="icon">
						<image class="imgicon" mode="heightFix" src="https://s4.ax1x.com/2022/02/16/HhHpZD.png"></image>
					</view>
					<view class="search">
						
					</view>
				</view>
				<view style="margin: 0rpx 30rpx; position: relative; height: 140rpx;">
					<view style="font-size: 60rpx;">
						服药提醒
					</view>
					<image class="add" mode="widthFix" src="https://s4.ax1x.com/2022/02/17/H4cX6J.png" @click="fuyaoItemOpen()"></image>
				</view>
				<view>
					<view v-for="(item,index) in fuyao" class="fuyaoItem">
						<view style="font-size: 50rpx;">{{item.name}}</view>
						<view style="font-size: 40rpx;">服药时间：{{item.time}}</view>
						<view style="font-size: 40rpx;">服药节点：{{item.type}}</view>
						<view style="font-size: 40rpx;">用量：{{item.yongliang}}</view>
						<image class="fuyaophoto" mode="widthFix" :src="item.photo"></image>
					</view>
				</view>
			</view>
			<view style="height: 100rpx;"></view>
		</scroll-view>
		<uni-popup ref="popup" type="center" :animation="true" :maskClick="true">
			<view style="padding: 40px; background-color: #f1e4cf;">
				<scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower"@scroll="scroll">
				
					<view>
						<view style="font-size: 50rpx;">
							添加服药提醒
						</view>
						<view style="font-size: 40rpx;padding: 20rpx 0rpx;">
							服药名称：
							<input class="fuyaomingcheng" placeholder="什么药呢？" placeholder-class="placeholder-color"/>
						</view>
						<view style="font-size: 40rpx;padding: 20rpx 0rpx;">
							服药时间：
							<view>
								<label class="radio"><radio color="#e69974" value="r1" :checked="fuyaoshijianxuanxiang == 1" @click="choose(1)"/>饭前</label>
								<label class="radio"><radio color="#e69974" value="r2" :checked="fuyaoshijianxuanxiang == 2" @click="choose(2)"/>饭后</label>
								<label class="radio"><radio color="#e69974" value="r3" :checked="fuyaoshijianxuanxiang == 3" @click="choose(3)"/>即服</label>
							</view>
						</view>
						
						<button style="background-color: #e69974;" type="primary" @click="DatePicker('datetime')">{{datetime}}</button>
						<mx-date-picker :show="showPicker" :type="type" :value="value" :show-tips="true" :begin-text="'入住'" :end-text="'离店'" :show-seconds="true" @confirm="ed" @cancel="ed" />
					
						<view style="font-size: 40rpx;padding: 20rpx 0rpx;">
							用量：
							<input class="fuyaomingcheng" placeholder="一次吃几片？" placeholder-class="placeholder-color"/>
						</view>
						
						<view style="font-size: 40rpx;padding: 20rpx 0rpx;">
							照片：
							<image v-if="fuyaoimg != ''" style="display: block;margin: 0 auto; width: 350rpx; height: 350rpx;" class="" mode="aspectFill" :src="fuyaoimg"></image>
							<view v-if="fuyaoimg == ''" class="add-image" @click="chooseImg">
								
							</view>
						</view>
					</view>
					
					<view style="height: 60rpx;"></view>
					<view class="paybutton" style="text-align: center; line-height: 110rpx; font-size: 44rpx;" @click="close">
							确认
					</view>
				</scroll-view>
			</view>
		</uni-popup>
	</view>
</template>

<script>
	import MxDatePicker from "@/components/mx-datepicker/mx-datepicker.vue";
	export default {
		components: {
		    MxDatePicker
		},
		data() {
			return {
				datetime: '2019/01/01 15:00:12',
				type: 'rangetime',
				value: '',
				index: 0,
				showPicker: false,
				fuyao: [
					{
						name: "降压药",//服药名称
						time: "2021",//服药时间
						type: "饭后",//类型 饭前饭后即服
						yongliang: "一次三片",//用量
						photo: "https://s4.ax1x.com/2022/02/17/H4cz01.png"//药品照片
					}
				],
				fuyaoshijianxuanxiang: 1,
				fuyaoimg: ""
			}
		},
		onLoad() {

		},
		methods: {
			fuyaoItemOpen(index) {
				this.fuyaoimg = '';
				this.$refs['popup'].open();
			},
			DatePicker(type){//显示
			    this.type = type;
			    this.showPicker = true;
				this.value = this[type];
			},
			ed(e) {//选择
			    this.showPicker = false;
			    if(e) {
			        this[this.type] = e.value; 
			        //选择的值
			        console.log('value => '+ e.value);
			        //原始的Date对象
			        console.log('date => ' + e.date);
			    }
			},
			close() {
				//添加服药接口
				this.$refs['popup'].close();
				uni.showToast({
					icon:'success',
					title:'添加成功！'
				})
			},
			choose(num) {
				this.fuyaoshijianxuanxiang = num;
			},
			chooseImg () {
				uni.chooseImage({
					count: 1,
					success:res=>{
						this.fuyaoimg = res.tempFilePaths;
					}
				})
			},
			navback() {
				uni.navigateBack();
			}
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
	.fuyaoItem {
		position: relative;
		padding-top: 20rpx;
		display: block;
		margin: 0 auto;
		width: 700rpx;
		height: 240rpx;
		background-image: url(https://s4.ax1x.com/2022/02/17/H4gjC8.png);
		background-position: left 0;
		background-repeat: no-repeat;
		background-size: 700rpx;
	}
	.fuyaoItem > view {
		margin-left: 40rpx;
	}
	.fuyaophoto {
		position: absolute;
		right: 40rpx;
		bottom: 20%;
		width: 200rpx;
	}
	.add {
		position: absolute;
		right: 0;
		top: 0;
		margin: 10rpx;
		width: 100rpx;
	}
	.paybutton {
		height: 140rpx;
		background-image: url(https://s4.ax1x.com/2022/02/16/H4uHG4.png);
		background-position: center 0;
		background-repeat: no-repeat;
		background-size: 300rpx;
	}
	.fuyaomingcheng {
		color: white;
		font-size: 34rpx;
		background-color: #e69974;		padding: 20rpx 0rpx; 
		border-radius: 14rpx;
	}
	.placeholder-color {
		color: white;
		text-align: center;
	}
	.add-image {
		background-color: #E4E6E7;
		padding: 90rpx;
		height: 100rpx;
		background-image: url(https://s4.ax1x.com/2022/02/17/H4cxmR.png);
		background-position: center center;
		background-repeat: no-repeat;
		background-size: 100rpx;
		width: 100rpx;
		display: block;
		margin: 0 auto;
	}
	.scroll-Y {
		height: 800rpx;
	}
	.back {
		height: 80rpx;
		background-image: url(https://s4.ax1x.com/2022/02/17/H4qfcn.png);
		background-position: left top;
		background-repeat: no-repeat;
		background-size: 80rpx;
		width: 80rpx;
	}
</style>
