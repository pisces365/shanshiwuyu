<template>
	<view class="content">
		<scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower"@scroll="scroll">
			<view class="topimg">
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
				<view class="selectbar" style="display: flex;">
					<view :class="page1?'topbuttonselected shequ':'shequ'" style="flex: 1; text-align: center;" @click="selectPage('1')">社区</view>
					<view :class="page2?'topbuttonselected shequ':'shequ'" style="flex: 1; text-align: center;" @click="selectPage('2')">专家咨询</view>
				</view>
				<view class="mainpage">
					<view v-if="page1">
						<view class="selectbar" style="display: flex;">
							<view :class="shequ1?'topbuttonselected shequbar':'shequbar'" style="flex: 1; text-align: center;" @click="selectmessage('1')">年龄区</view>
							<view :class="shequ2?'topbuttonselected shequbar':'shequbar'" style="flex: 1; text-align: center;" @click="selectmessage('2')">病情区</view>
							<view :class="shequ3?'topbuttonselected shequbar':'shequbar'" style="flex: 1; text-align: center;" @click="selectmessage('3')">地域区</view>
						</view>
						<view>
							<view v-for="(item,index) in shequ" class="shequitem" v-if="shequ1?item.type==1:(shequ2?item.type==2:item.type==3)">
								<view class="shequitemimgborder">
									<view style="font-size: 40rpx;">
										<text>
											{{item.name}}
										</text>
										<text style="display: inline-block; margin-left: 10rpx; background-color: #f1e4cf; border-radius: 10rpx;">
											{{item.zhicheng}}
										</text>
									</view>
									<view style="font-size: 32rpx; color: #6A6A6A;">
										{{item.date}}
									</view>
								</view>
								<view class="comment">
									{{item.message}}
								</view>
								<view style="display: block;float: right;">
									<view style="display: inline-block;" class="icondianzan"></view>
									<view style="display: inline-block;" class="iconpinglun"></view>
									<view style="display: inline-block;" class="iconfenxiang"></view>
								</view>
								<view style="display: block;height: 80rpx;"></view>
							</view>
						</view>
					</view>
					<view v-if="page2" class="zhuanjiapage">
						<view v-for="(item,index) in doctor" class="doctorItem" style="display: flex;" >
							<view class="head" @click="docterItemOpen(index)">
								<image class="headicon" mode="heightFix" :src="item.headicon"></image>
							</view>
							<view class="name" style="font-size: 50rpx; flex:3;" @click="docterItemOpen(index)">
								{{item.name}}医生
							</view>
							<view class="message">
								<image class="messageicon" mode="heightFix" :src="item.messageicon"></image>
							</view>
							<view class="phone">
								<image class="phoneicon" mode="heightFix" :src="item.phoneicon"></image>
							</view>
						</view>
						<uni-popup ref="popup" type="center" :animation="true" :maskClick="true" @change="change">
							<view style="padding: 20px; background-color: #f1e4cf;">
								<view class="head">
									<image style="display: block;margin: 0 auto;" class="headiconpop" mode="heightFix" :src="doctor[docterSelect].headicon"></image>
								</view>
								<view class="name" style="font-size: 50rpx; text-align: center;">
									{{doctor[docterSelect].name}}医生
								</view>
								<view>
									<view style="font-size: 40rpx;padding: 20rpx 0rpx;">
										预约时间：{{datetime}}
									</view>
									<button style="background-color: #e69974;" type="primary" @click="DatePicker('datetime')">选择预约时间</button>
									<mx-date-picker :show="showPicker" :type="type" :value="value" :show-tips="true" :begin-text="'入住'" :end-text="'离店'" :show-seconds="true" @confirm="ed" @cancel="ed" />
								</view>
								<view>
									<view style="font-size: 40rpx;padding: 20rpx 0rpx;">
										预约时长：{{timeLong[index]}}
									</view>
									<picker style="background-color: #e69974; padding: 20rpx 0rpx; border-radius: 14rpx;" @change="timeLongPickerChange" :value="index" :range="timeLong">
									    <view class="uni-input" style="text-align: center; font-size: 40rpx; color: white;">选择预约时长</view>
									</picker>
								</view>
								<view style="height: 60rpx;"></view>
								<view class="paybutton" style="text-align: center; line-height: 110rpx; font-size: 44rpx;" @click="close">
										确认支付
								</view>
							</view>
						</uni-popup>
					</view>
				</view>
			</view>
			<view style="height: 100rpx;"></view>
		</scroll-view>
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
				page1: true,
				page2: false,
				shequ1: true,
				shequ2: false,
				shequ3: false,
				shequ: [
					{
						img: "https://s4.ax1x.com/2022/02/16/HhXuPe.png",
						name: "荷花",
						zhicheng: "专家",
						date: "2022/2/14",
						message: "发表了一些评论1",
						type: 1
					},
					{
						img: "https://s4.ax1x.com/2022/02/16/HhXuPe.png",
						name: "桃花",
						zhicheng: "专家",
						date: "2022/2/14",
						message: "发表了一些评论1",
						type: 1
					},
					{
						img: "https://s4.ax1x.com/2022/02/16/HhXuPe.png",
						name: "荷花",
						zhicheng: "专家",
						date: "2022/2/14",
						message: "发表了一些评论2",
						type: 2
					},
					{
						img: "https://s4.ax1x.com/2022/02/16/HhXuPe.png",
						name: "荷花",
						zhicheng: "专家",
						date: "2022/2/14",
						message: "这是个评论",
						type: 3
					}
				],
				doctor: [
					{
						headicon: "https://s4.ax1x.com/2022/02/16/HhXuPe.png",
						name: "",
						messageicon: "https://s4.ax1x.com/2022/02/16/HhXQxA.png",
						phoneicon: "https://s4.ax1x.com/2022/02/16/HhX3rt.png"
					},
					{
						headicon: "https://s4.ax1x.com/2022/02/16/HhXuPe.png",
						name: "",
						messageicon: "https://s4.ax1x.com/2022/02/16/HhXQxA.png",
						phoneicon: "https://s4.ax1x.com/2022/02/16/HhX3rt.png"
					},
					{
						headicon: "https://s4.ax1x.com/2022/02/16/HhXuPe.png",
						name: "",
						messageicon: "https://s4.ax1x.com/2022/02/16/HhXQxA.png",
						phoneicon: "https://s4.ax1x.com/2022/02/16/HhX3rt.png"
					}
				],
				docterSelect: 0,
				showPicker: false,
				datetime: '2019/01/01 15:00:12',
				type: 'rangetime',
				value: '',
				index: 0,
				timeLong: ["10分钟 ￥5","20分钟 ￥10","30分钟 ￥15","60分钟 ￥20"]
			}
		},
		onLoad() {
 
		},
		methods: {
			selectPage(num) {
				switch(num) {
					case '1': this.page1 = true; this.page2 = false; break;
					case '2': this.page1 = false; this.page2 = true; break;
				}
			},
			selectmessage(num) {
				switch(num) {
					case '1': this.shequ1 = true; this.shequ2 = false; this.shequ3 = false; break;
					case '2': this.shequ1 = false; this.shequ2 = true; this.shequ3 = false; break;
					case '3': this.shequ1 = false; this.shequ2 = false; this.shequ3 = true; break;
				}
			},
			docterItemOpen(index) {
				this.docterSelect = index;
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
			timeLongPickerChange: function(e) {
			    console.log('picker发送选择改变，携带值为', e.target.value)
			    this.index = e.target.value
			},
			close() {
				this.$refs['popup'].close();
				uni.showToast({
					icon:'success',
					title:'支付成功！'
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
	.shequ,
	.zhuanjiazixun {
		background-color: #e4e6e7;
		padding: 20rpx 0;
		font-size: 50rpx;
		border-top-left-radius: 20rpx;
		border-top-right-radius: 20rpx;
		border-bottom: 4rpx solid #bebebe;
	}
	
	.topbuttonselected {
		background-color: #e69974 !important;
	}
	
	.shequbar {
		background-color: #e4e6e7;
		margin: 20rpx 20rpx;
		padding: 60rpx 0rpx;
		font-size: 50rpx;
	}
	
	.headicon {
		height: 100rpx;
		width: 100rpx;
	}
	.headiconpop {
		height: 160rpx;
		width: 160rpx;
	}
	.messageicon {
		height: 80rpx;
		width: 80rpx;
	}
	.phoneicon {
		height: 80rpx;
		width: 80rpx;
	}
	.doctorItem > view {
		flex: 1;
		padding: 20rpx 20rpx;
		border-top: 1px solid #BEBEBE;
	}
	.paybutton {
		height: 140rpx;
		background-image: url(https://s4.ax1x.com/2022/02/16/H4uHG4.png);
		background-position: center 0;
		background-repeat: no-repeat;
		background-size: 300rpx;
	}
	.shequitemimgborder {
		padding-left: 120rpx;
		height: 100rpx;
		background-image: url(https://s4.ax1x.com/2022/02/16/HhXuPe.png);
		background-position: 0 0;
		background-repeat: no-repeat;
		background-size: 100rpx;
	}
	.comment {
		margin-top: 20rpx;
		font-size: 34rpx;
		margin-bottom: 20rpx;
	}
	.shequitem {
		background-color: #fff9ef;
		padding: 20rpx;
		margin-bottom: 20rpx;
	}
	.icondianzan {
		height: 60rpx;
		background-image: url(https://s4.ax1x.com/2022/02/17/H5ShwR.png);
		background-position: 0 0;
		background-repeat: no-repeat;
		background-size: 60rpx;
		width: 100rpx;
	}
	.iconpinglun {
		height: 60rpx;
		background-image: url(https://s4.ax1x.com/2022/02/17/H5SIFx.png);
		background-position: 0 0;
		background-repeat: no-repeat;
		background-size: 60rpx;
		width: 100rpx;
	}
	.iconfenxiang {
		height: 60rpx;
		background-image: url(https://s4.ax1x.com/2022/02/17/H5S4T1.png);
		background-position: 0 0;
		background-repeat: no-repeat;
		background-size: 60rpx;
		width: 100rpx;
	}
</style>
