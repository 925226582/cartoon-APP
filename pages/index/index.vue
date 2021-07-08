<template>
	<view id="home">
		<uni-nav-bar statusBar="true">
			<view class="nav-bar-logo">
				<image src="../../static/icon/logo.png" mode="aspectFit"></image>
			</view>
		</uni-nav-bar>
		<view class="tbox">
			<view class="tbox-cont">
				<view class="wcont">
					<!-- 主导航条 -->
					<view class="tnavs">
						<view class="tnavs-l" @tap="showmenu">
							<image src="../../static/icon/icon01.png" mode="aspectFit"></image>
						</view>
						<view class="tnavs-c">分类</view>
						<view class="tnavs-r">
							<image src="../../static/icon/icon02.png" mode="aspectFit"></image>
						</view>
					</view>
				</view>
			</view>
		</view>
		<!-- 轮播推荐条 -->
		<view class="recommend-swiper-box">
			<view class="wcont">
				<view class="recommend-swiper">
					<uni-swiper-dot :info="recommend" :current="current" mode="round" :dotsStyles="dotsStyles">
						<swiper class="swiper-box" @change="recommendChange" autoplay="true" circular="true">
							<swiper-item v-for="(item ,index) in recommend" :key="index">
								<navigator :url="item.url" hover-class="none">
									<image :src="item.img" mode="aspectFill"></image>
								</navigator>
							</swiper-item>
						</swiper>
					</uni-swiper-dot>
				</view>
			</view>
		</view>
		<view class="container-ctrl">
			<view class="container-ctrl-box" @tap="showtap">
				<view class="container-btn" :class="{on:showtapindex==1}" data-index="1">发现</view>
				<view class="container-btn" :class="{on:showtapindex==2}" data-index="2">推荐</view>
			</view>
		</view>
		<view class="container">
			<view class="container-item" v-if="showtapindex==1" style="background-color: #fff;">
				<view class="wcont">
					<!-- 推荐 -->
					<view class="listbox">
						<book-list col="3" booknumse="false"></book-list>
						<view class="vmore-box">
							<navigator class="vmore" url="" hover-class="nhover">
								<text class="iconfont icon-Category"></text>
								<text>查看更多</text>
							</navigator>
						</view>
					</view>
					<!-- 今日更新 -->
					<view class="listbox">
						<view class="tytitle">
							<text>今日更新</text>
						</view>
						<book-list col="3" booknumse="false"></book-list>
						<view class="vmore-box">
							<navigator class="vmore" url="" hover-class="nhover">
								<text class="iconfont icon-Category"></text>
								<text>查看更多</text>
							</navigator>
						</view>
					</view>
					<!-- 排行榜 -->
					<view class="listbox">
						<view class="tytitle">
							<text>排行榜</text>
						</view>
						<view class="rankctrl">
							<view class="rankbtn on">人气榜</view>
							<view class="rankbtn">黑马榜</view>
							<view class="rankbtn">新作榜</view>
						</view>
						<book-list rank="true" col="3" booknumse="false"></book-list>
						<view class="vmore-box">
							<navigator class="vmore" url="" hover-class="nhover">
								<text class="iconfont icon-Category"></text>
								<text>查看更多</text>
							</navigator>
						</view>
					</view>
				</view>
			</view>
			<view class="container-item" v-if="showtapindex==2" style="background-color: #ffcc00;">
				<view class="wcont">
					<book-list col="2" booknumse="true"></book-list>
				</view>
			</view>
		</view>
		<view class="copyright">© DAYADAYA.COM</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				recommend: [{
						url: "aaa",
						img: "/static/temp/ls01.jpg"
					},
					{
						url: "aaa",
						img: "/static/temp/ls01.jpg"
					}
				], //推荐轮播图
				current: 0, //轮播图索引
				dotsStyles: {
					width: 6,
					bottom: 0,
					backgroundColor: "#000000",
					selectedBackgroundColor: "#000000",
					border: "none",
					selectedBorder: "none"
				}, //轮播图指示点
				showtapindex: 1, //切换视图索引值
			}
		},
		methods: {
			//推荐轮播图
			recommendChange(e) {
				this.current = e.detail.current;
			},
			//打开菜单
			showmenu() {
				uni.getSubNVueById('menus').show('slide-in-left', 200);
			},
			//切换视图
			showtap(e) {
				let _ind = e.target.dataset.index;
				if (_ind && _ind != this.showtapindex) {
					this.showtapindex = _ind;
					this.getlist(Number(_ind))
				}
			},
			//获取数据  根据参数不同执行不同的获取方法
			getlist(ind) {
				uni.showLoading({
					mask: true,
					title: '加载中'
				});
				setTimeout(function() {
					uni.hideLoading();
				}, 2000);
				switch (ind) {
					case 1:
						this.getfinds();
						break;
					case 2:
						this.gettops();
						break;
				}
			},
			//获取发现页的内容
			getfinds() {
				console.log("获取发现页的内容")
			},
			// 获取推荐
			gettops() {
				console.log("获取推荐")
			}
		}
	}
</script>

<style lang="scss">
	#home {
		width: 100%;
	}

	.nav-bar-logo {
		image {
			height: 50rpx;
		}
	}

	.tbox {
		position: sticky;
		top: 0;
		z-index: 22;
		background-color: #020202;

		.tbox-cont {
			background-color: #ffcc00;
			border-radius: 32rpx 32rpx 0 0;
		}

	}

	.tnavs {
		background-color: #ffcc00;
		display: flex;
		align-items: center;
		justify-content: space-between;
		height: 120rpx;


		.tnavs-c {
			font-size: 24rpx;
			color: #ffff00;
			background-color: #e8ba00;
			border-radius: 10000px;
			padding: 10rpx 25rpx;
		}

		.tnavs-l,
		.tnavs-r {
			& image {
				display: block;
				width: 64rpx;
				height: 64rpx;
			}
		}
	}

	// 推荐轮播
	.recommend-swiper-box {
		background-color: #ffcc00;
		padding-top: 20rpx;

		.recommend-swiper {
			padding-bottom: 34rpx;

			.swiper-box {
				height: 280rpx;
				border-radius: 32rpx;
				overflow: hidden;

				navigator,
				image {
					display: block;
					width: 100%;
					height: 100%;
				}
			}
		}
	}


	// 切换按钮
	.container-ctrl {
		position: sticky;
		top: 120rpx;
		z-index: 12;
		padding: 0 30rpx;
		box-sizing: border-box;
		z-index: 22;

		&::before {
			position: absolute;
			content: "";
			width: 100%;
			height: 50%;
			top: 0;
			left: 0;
			background-color: #ffcc00;
		}

		.container-ctrl-box {
			display: flex;
			background: #fff;
			align-items: center;
			justify-content: center;
			height: 100rpx;
			border-radius: 32rpx;
			position: relative;
			z-index: 2;
		}

		.container-btn {
			font-size: 40rpx;
			color: #adaba3;
			position: relative;
			margin: 0 20rpx;
			line-height: 1;
			padding: 5rpx 0;

			&.on {
				color: #000;
				font-weight: bold;

				&::before {
					content: "";
					position: absolute;
					bottom: 0;
					left: 0;
					width: 100%;
					height: 10rpx;
					background-color: #ffcc00;
					z-index: -1;
				}
			}
		}
	}

	// 内容区
	.container {
		margin-top: -50rpx;

		.container-item {
			padding-top: 70rpx;
		}
	}

	.vmore-box {
		padding: 40rpx 0;
	}

	.vmore {
		border-radius: 100px;
		background-color: #f2f2f2;
		width: 100%;
		padding: 20rpx 0;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 28rpx;
		color: #000;

		.iconfont {
			font-size: 36rpx;
			margin-right: 20rpx;
			color: #ffb400;
		}
	}

	// 通用title
	.tytitle {
		display: flex;
		align-items: center;
		justify-content: center;
		padding: 30rpx 0;
		margin-bottom: 15rpx;

		&::before,
		&::after {
			content: "";
			width: 35rpx;
			height: 35rpx;
			background-image: url(data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAABYAAAAZCAYAAAA14t7uAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyZpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuNi1jMTM4IDc5LjE1OTgyNCwgMjAxNi8wOS8xNC0wMTowOTowMSAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENDIDIwMTcgKFdpbmRvd3MpIiB4bXBNTTpJbnN0YW5jZUlEPSJ4bXAuaWlkOjJGQzE4RTNDQzlCMTExRUJCODlBQTREM0MzMEU1QTdGIiB4bXBNTTpEb2N1bWVudElEPSJ4bXAuZGlkOjJGQzE4RTNEQzlCMTExRUJCODlBQTREM0MzMEU1QTdGIj4gPHhtcE1NOkRlcml2ZWRGcm9tIHN0UmVmOmluc3RhbmNlSUQ9InhtcC5paWQ6MkZDMThFM0FDOUIxMTFFQkI4OUFBNEQzQzMwRTVBN0YiIHN0UmVmOmRvY3VtZW50SUQ9InhtcC5kaWQ6MkZDMThFM0JDOUIxMTFFQkI4OUFBNEQzQzMwRTVBN0YiLz4gPC9yZGY6RGVzY3JpcHRpb24+IDwvcmRmOlJERj4gPC94OnhtcG1ldGE+IDw/eHBhY2tldCBlbmQ9InIiPz6ni6OZAAACQElEQVR42pxWTUhVQRQ+115ZLlwooavCReBCEStoEW5E3Uig4SJxk5uoUDPXlfi3ceFvINHCNiGpSCAuDErQVqEEIU/FhdFKgxBcZKV2+859576G884gvA8+3syZO9+dOX/vBmEY0qloDXwrF8BG+Z0D9yPrZEgJWgsoS+SCS+ANmT8Dr4I/eJJD2aPDEWVcAu/EE0u4GdwFf4KjoHWlYvCJYT/yCZeCr8Ai8RufqsUQGADzlY1dMOMT5hOeU7ZyNb8O3jVe9jQdPCVcD9YZGz44Y3bLiHGgdfCla4gfOAsOG6LvwUXl/5ueQB5bwrxwRT3MD3YqmxWwt5J2pIUvSg5qvJAruris5r/AroydCwEKhKjHE+Fu42XTKnCD4E40aqIzkk174AkL3zIEeimZqqAI1ekwPhChCgnqhIhy5szLjXi9IQhXaRmDKhXhSggfe2vOzZOm6NafwTLHusI+bk9fh+hrVBApUV57CM5K0M57XnNfiTJK+MSM//5J0oks9qigckW2RqOCtK0Q3JJfFxMp4WTGKUrADelgMQ7BPCU8DrapvQecujl0zezHQ0o0dpOLMnFDZuCJvlvdjXOgwbD3Gy9PKNs2OGY1oYQ0Io2P4JQz555Sazz3OG6dWvieEeG/ssH1WY0h+o5rzupuBeIfjUlwVdm+qPkf8JHVhFKpnpk2B57G8xp8Lr1iT8p8U/vUGsfok78pjVAKq91XnO6J34DfnPknydOskFAdrRK8LcXA3wm/zV31p3+L/BNgANOJelXVpbLnAAAAAElFTkSuQmCC);
			background-size: contain;
			background-repeat: no-repeat;
			background-position: center;
		}

		text {
			font-size: 40rpx;
			color: #000000;
			padding: 0 30rpx;
		}
	}

	// rankbtn
	.rankctrl {
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 0 30rpx;
		box-sizing: border-box;
		margin-bottom: 40rpx;

		.rankbtn {
			padding: 10rpx 20rpx;
			font-size: 32rpx;
			color: #000000;
			border-radius: 1000px;

			&.on {
				background-color: #ffcc00;
				font-weight: bold;
			}
		}
	}

	.copyright {
		font-size: 24rpx;
		color: #888888;
		text-align: center;
		padding: 30rpx 0;
	}
</style>
