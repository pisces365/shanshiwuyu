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
				<view>
					<scroll-view scroll-x="true" class="quick_scene_bar">
					  <block v-for="(item, index) in scene" :key="index" >
					    <view class="bar" :style="'background-image: url('+item.img+');'" @click="nav(index)">
							<view class="bar_sign" >
								{{item.sign}}
							</view>
						</view>
					  </block>
					</scroll-view>
				</view>
				<view class="selectbar" style="display: flex;">
					<view :class="page1?'topbuttonselected shequ':'shequ'" style="flex: 1; text-align: center;" @click="selectPage('1')">猜您喜欢</view>
					<view :class="page2?'topbuttonselected shequ':'shequ'" style="flex: 1; text-align: center;" @click="selectPage('2')">今日特价</view>
				</view>
				<view class="secondHandItems">
					<view class="secondHandItem">
						<navigator url="../../pagesMarket/buy/buy?id=0">
							<viewx>
								<image class="secondHandImage" src="http://p1362.bvimg.com/10465/a7d5ea952a98180e.png"
									style="width: 100%;" mode="aspectFill"></image>
							</viewx>
							<view>
								<text class="goods-name">世界金奖茶</text>
							</view>
							<view class="">
								<text class="brand-and-condition">狗牯脑</text>
								<text class="brand-and-condition">|</text>
								<text class="brand-and-condition">一级红茶100g</text>
							</view>
							<view class="" style="margin-bottom: 10rpx;">
								<text class="price-now">￥139</text>
								<text class="price-before">￥150</text>
								<text class="discount">已减￥11</text>
							</view>
						</navigator>
						<navigator url="../../pagesMarket/buy/buy?id=1">
							<viewx>
								<image class="secondHandImage" src="http://p1362.bvimg.com/10465/19501074f893abf8.jpg"
									style="width: 100%;" mode="aspectFill"></image>
							</viewx>
							<view>
								<text class="goods-name">迁西栗蘑菇干舞茸新鲜栗蘑灰树</text>
							</view>
							<view class="">
								<text class="brand-and-condition">干货 | 优质农特产</text>
							</view>
							<view class="" style="margin-bottom: 10rpx;">
								<text class="price-now">￥129</text>
								<text class="price-before">￥200</text>
								<text class="discount">已减￥71</text>
							</view>
						</navigator>
						<navigator url="../../pagesMarket/buy/buy?id=2">
							<viewx>
								<image class="secondHandImage" src="http://p1362.bvimg.com/10465/6d92b7a5dcd30b55.jpg"
									style="width: 100%;" mode="aspectFill"></image>
							</viewx>
							<view>
								<text class="goods-name">九龙乡露天生长椴木黑木耳</text>
							</view>
							<view class="">
								<text class="brand-and-condition">农家自产</text>
								<text class="brand-and-condition">|</text>
								<text class="brand-and-condition">纯天然</text>
							</view>
							<view class="" style="margin-bottom: 10rpx;">
								<text class="price-now">￥58</text>
								<text class="price-before">￥74</text>
								<text class="discount">已减￥16</text>
							</view>
						</navigator>
					</view>
					<view class="secondHandItem">
						<viewx>
							<image src="http://p1362.bvimg.com/10465/515b3af70f8568ab.png"
								style="width: 100%; height: 200rpx; border-radius: 20rpx; margin-bottom: 10rpx;">
							</image>
						</viewx>
						<navigator url="../../pagesMarket/buy/buy?id=3">
							<viewx>
								<image class="secondHandImage" src="http://p1362.bvimg.com/10465/bf61e2929e325d5a.jpg"
									style="width: 100%;" mode="aspectFill"></image>
							</viewx>
							<view>
								<text class="goods-name">头一锅单县羊肉汤</text>
							</view>
							<view class="">
								<text class="brand-and-condition">自家羊肉熬制</text>
								<text class="brand-and-condition">|</text>
								<text class="brand-and-condition">火热生活</text>
							</view>
							<view class="" style="margin-bottom: 10rpx;">
								<text class="price-now">￥139</text>
								<text class="price-before">￥160</text>
								<text class="discount">已减￥21</text>
							</view>
						</navigator>
						<navigator url="../../pagesMarket/buy/buy?id=4">
							<viewx>
								<image class="secondHandImage" src="http://p1362.bvimg.com/10465/a47c31ec00f915e9.jpg"
									style="width: 100%;" mode="aspectFill"></image>
							</viewx>
							<view>
								<text class="goods-name">五峰源高山红茶</text>
							</view>
							<view class="">
								<text class="brand-and-condition">现货</text>
								<text class="brand-and-condition">|</text>
								<text class="brand-and-condition">新鲜采摘</text>
							</view>
							<view class="" style="margin-bottom: 10rpx;">
								<text class="price-now">￥99</text>
								<text class="price-before">￥129</text>
								<text class="discount">已减￥30</text>
							</view>
						</navigator>
						<navigator url="../../pagesMarket/buy/buy?id=5">
							<viewx>
								<image class="secondHandImage" src="http://p1362.bvimg.com/10465/2fdd18d415f5b95c.jpg"
									style="width: 100%;" mode="aspectFill"></image>
							</viewx>
							<view>
								<text class="goods-name">纯手工香油辣椒酱</text>
							</view>
							<view class="">
								<text class="brand-and-condition">现货</text>
								<text class="brand-and-condition">|</text>
								<text class="brand-and-condition">自家47天酿制</text>
							</view>
							<view class="" style="margin-bottom: 10rpx;">
								<text class="price-now">￥49</text>
								<text class="price-before">￥69</text>
								<text class="discount">已减￥20</text>
							</view>
						</navigator>
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
				scene: [
					{
						sign: '外卖',
						img: 'https://s1.ax1x.com/2022/03/30/qgiN7R.png'
					},
					{
						sign: '团购',
						img: 'https://s1.ax1x.com/2022/03/30/qgitB9.png'
					},
					{
						sign: '闪惠',
						img: 'https://s1.ax1x.com/2022/03/30/qgif4P.png'
					},
					{
						sign: '专属会员卡',
						img: 'https://s1.ax1x.com/2022/03/30/qgFsP0.png'
					},
					{
						sign: '扫码识别',
						img: 'https://s1.ax1x.com/2022/03/30/qgA49x.png'
					},
				],
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
			nav(index) {
				if(index == 4) {
					uni.navigateTo({
						url: "scan/scan"
					})
				}
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
	.quick_scene_bar {
	    white-space: nowrap; 
	    width: 700rpx;
	    height: 180rpx;
	    padding-top: 20rpx;
		padding-bottom: 20rpx;
	    margin: 0 auto;
		padding-left: 0rpx;
		/* margin-right: 50rpx; */
	}
	.bar {
		display: inline-block;
		background-color: rgba (0, 0, 0, 0);
		padding: 20rpx 30rpx;
		margin-right: 40rpx;
		border-radius: 20rpx;
		padding-top: 100rpx;
		/* box-shadow: 10rpx 10rpx 30rpx #C8C7CC; */
		/* background-image: url(https://s1.ax1x.com/2022/03/29/q6Zkfx.png); */
		background-repeat: no-repeat;
		background-position: center 10rpx;
		background-size: 100rpx;
	}
	::-webkit-scrollbar{
	    display: none;
	}
	
	.bar_sign {
		/* font-weight: 600; */
		font-size: 26rpx;
		color: #999999;
	}
	
	.shequ,
	.zhuanjiazixun {
		/* background-color: #e4e6e7; */
		padding: 20rpx 0;
		font-size: 30rpx;
		border-top-left-radius: 20rpx;
		border-top-right-radius: 20rpx;
		/* border-bottom: 4rpx solid #bebebe; */
	}
	
	.topbuttonselected {
		background-color: #e69974 !important;
	}
	
	.shequbar {
		/* background-color: #e4e6e7; */
		margin: 20rpx 20rpx;
		padding: 60rpx 0rpx;
		font-size: 50rpx;
	}
</style>

<style>


	page {
		/* background-color: #efefef; */
	}

	.tk {
		margin: 0 auto;
	}

	.sh {
		background-image: url(http://p1362.bvimg.com/10465/2e34886d83fd8dbe.png);
		background-repeat: no-repeat;
		background-size: 900rpx;
		background-position: center 50rpx;
	}

	.new-sh {
		display: inline-block;
		padding: 10rpx 14rpx;
		border-radius: 100rpx;
		color: white;
		margin: 40rpx 0;
		margin-bottom: 70rpx;
	}

	.secondHandItems navigator {
		background-color: #fff;
		border-radius: 20rpx;
		padding-bottom: 10rpx;
		margin-bottom: 20rpx;
	}

	.secondHandItems navigator view {
		margin-left: 10rpx;

	}

	.sh-image {
		width: 100rpx;
		height: 100rpx;
		display: block;
		margin: 0 auto;
	}

	.title {
		margin-top: 14rpx;
		font-size: 30rpx;
		text-align: center;
	}

	.discribe {
		font-size: 28rpx;
		color: #A6A6A6;
		text-align: center;
	}

	.icon {
		flex: 1;
		margin: 0 30rpx;
	}

	.search {
		padding: 14rpx 20rpx;
		margin: 0rpx 30rpx;
		background-color: rgb(243, 243, 243);
		border-radius: 20rpx;
		font-size: 28rpx;
		/* width: 100%; */
	}



	.secondHandItems {
		display: flex;
	}

	.secondHandItem {
		flex: 1;
		margin: 10rpx;
		/* display: flex; */
	}

	.secondHandImage {
		/* flex: 1; */
		border-top-left-radius: 20rpx;
		border-top-right-radius: 20rpx;
	}

	.price-now {
		font-size: 30rpx;
		color: rgb(243, 153, 18);
	}

	.price-before {
		margin-left: 8rpx;
		color: rgb(243, 153, 18);
		font-size: 24rpx;
		text-decoration: line-through;
	}

	.discount {
		margin-left: 8rpx;
		color: rgb(243, 153, 18);
		background-color: rgba(243, 153, 18, 0.1);
		font-size: 24rpx;
		padding: 6rpx;
		margin-right: 10rpx;
	}

	.goods-name {
		font-weight: bold;
		margin-right: 14rpx;
		font-size: 30rpx;
	}

	.brand-and-condition {
		font-size: 24rpx;
		color: #A6A6A6;
		margin: 0 8rpx;
	}

	.topImage {
		border-radius: 40rpx;
		margin: 30rpx;
		margin-top: 0;
		margin-bottom: 0;
		display: block;
		width: 690rpx;
		box-shadow: 0rpx 10rpx 30rpx #eeefee;
	}

	.top {
		padding-top: 30rpx;
		/* box-shadow: 0rpx 10rpx 30rpx #dcdddc; */
		/* background-color: white; */
		z-index: 100;
		/* float: left; */
		width: 100%;
		/* position: fixed; */
	}

	.index {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.index-swiper {
		height: 360rpx;
		width: 670rpx;
		margin: 24rpx 0 16rpx 0;
		border-radius: 20rpx;
		overflow: hidden;
	}

	.index-swiper-image image {
		height: 360rpx;
		width: 720rpx;
	}

	.index-blog {
		background: white;
		border-radius: 20rpx;
		margin: 10rpx 10rpx;
		margin-bottom: 10rpx;
		width: 670rpx;
		height: 120rpx;
		display: flex;
		flex-direction: row;
	}

	.index-blog-left {
		margin-left: 20rpx;
		width: 120rpx;
	}

	.index-blog-left image {
		width: 118rpx;
		height: 118rpx;
	}

	.index-blog-center-line {
		background: rgba(0, 0, 0, .3);
		height: 66rpx;
		width: 4rpx;
	}

	.index-blog-center {
		height: 100%;
		width: 4rpx;
		display: flex;
		align-items: center;
		justify-content: center;
		margin-left: 10rpx;
	}

	.index-blog-right {
		margin: 14rpx 16rpx 14rpx 14rpx;
		margin-left: 20rpx;
		display: flex;
		flex-direction: column;
		position: relative;
		flex: 1;

	}

	.index-blog-right-top {}

	.index-blog-right-top text {
		font-size: 26rpx;
		color: #3f3f3f;
	}

	.index-blog-right-bottom {
		position: absolute;
		top: 40rpx;
	}

	.index-blog-right-bottom text {
		font-size: 22rpx;
		color: #B8B9B8;


	}

	.index-blog-right-icon {
		position: absolute;
		top: 20rpx;
		right: 0rpx;
	}

	.index-blog-right-icon text {
		color: #00aa7f;
		font-size: 44rpx;
	}

	.index-VillageParty {
		width: 670rpx;
		/* height: 500rpx; */
		margin: 10rpx;
		/* background: green; */
	}

	.index-ServieceToPeople {
		margin-top: 10rpx;
		width: 670rpx;
		height: 480;
	}

	.index-VillageParty-title,
	.index-ServieceToPeople-title,
	.index-polling-title {
		display: flex;
		flex-direction: row;
		align-items: center;
	}

	.index-VillageParty-title-image image,
	.index-polling-title-image image {
		height: 100rpx;
		width: 100rpx;
	}

	.index-VillageParty-title text {
		margin-left: 14rpx;
		font-size: 34rpx;
	}

	.index-VillageParty-content-onePart {
		display: flex;
		flex-direction: row;
		flex-wrap: wrap;
		align-items: center;
		justify-content: center;
		margin-bottom: 20rpx;

	}

	.index-VillageParty-content-onePart-left {
		width: 300rpx;
		height: 114rpx;
		background: white;
		border-radius: 20rpx;
		margin: 0 16rpx;
		position: relative;
	}

	.index-VillageParty-content-onePart-noShow {
		width: 300rpx;
		height: 114rpx;
		/* background: white; */
		border-radius: 20rpx;
		margin: 0 16rpx;
		position: relative;
	}

	.funcion-top {
		padding: 10rpx 0 4rpx 20rpx;
	}

	.funcion-top text {
		font-size: 30rpx;
		color: #3f3f3f;
	}

	.funcion-bottom {
		position: absolute;
		top: 44rpx;
		padding: 0 0 4rpx 20rpx;
	}

	.funcion-bottom text {
		font-size: 20rpx;
		color: #B3B4B3;
	}

	.function-image {
		position: absolute;
		height: 114rpx;
		width: 114rpx;
		top: 0;
		right: 8rpx;
	}

	.function-image image {
		width: 100%;
		height: 100%;
	}

	.index-polling {
		width: 670rpx;
		height: 240rpx;
	}
</style>
