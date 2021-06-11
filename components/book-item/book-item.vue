<template>
	<view class="bookitem">
		<view class="bookpic">
			<view class="bookno" v-if="rank=='true'">96</view>
			<image class="bookimg" src="../../static/temp/ls02.jpg" mode="aspectFill"></image>
			<view class="booktips">1206 关注</view>
		</view>
		<view class="bookinfo">
			<view class="booktit">诛心之罪</view>
			<view class="booktype">
				<text class="booknumse" v-if="booknumse=='true'">1125 关注</text>
				<text :class="{on:booknumse=='true'}">剧情 古风 唯美</text>
			</view>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			booknumse: {
				type: [String, Boolean],
				default: false
			},
			rank: {
				type: [String, Boolean],
				default: false
			}
		},
		data() {
			return {

			}
		},
		methods: {

		}
	}
</script>

<style lang="scss" scoped>
	.bookitem {
		.bookpic {
			position: relative;
			overflow: hidden;
			border-radius: 25rpx;
			padding-bottom: 130%;

			.bookno {
				position: absolute;
				right: 0;
				top: 0;
				background-color: #fff;
				border-radius: 0 0 0 16rpx;
				width: 40rpx;
				line-height: 40rpx;
				text-align: center;
				font-size: 22rpx;
				color: #cc3333;
				z-index: 3;
				font-weight: bold;
			}

			.bookimg {
				position: absolute;
				top: 0;
				left: 0;
				width: 100%;
				height: 100%;
			}

			.booktips {
				position: absolute;
				bottom: 10rpx;
				left: 50%;
				transform: translateX(-50%);
				border-radius: 1000px;
				background-color: #ffcc00;
				font-size: 20rpx;
				color: #000;
				padding: 5rpx 15rpx;
				z-index: 3;
				white-space: nowrap;
			}
		}

		.bookinfo {
			padding: 20rpx 0;

			.booktit {
				font-size: 32rpx;
				color: #000;
				overflow: hidden;
				text-overflow: ellipsis;
				white-space: nowrap;
			}

			.booktype {
				font-size: 22rpx;
				color: #ababa3;
				overflow: hidden;
				text-overflow: ellipsis;
				white-space: nowrap;
				margin-top: 5rpx;

				.on {
					color: #000000;
				}

				.booknumse {
					color: #ffcc00;
					background-color: #000000;
					border-radius: 1000px;
					padding: 5rpx 15rpx;
					margin-right: 10rpx;
				}
			}
		}
	}
</style>
