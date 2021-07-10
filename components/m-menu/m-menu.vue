<template>
	<view class="menus" id="menus">
		<!-- 用户 -->
		<navigator url="" hover-class="nhover" class="user">
			<view class="user-l">
				<view class="user-img">
					<image class="uimg" src="/static/icon/icon01.png" mode="aspectFill"></image>
				</view>
				<text class="user-name">mynammynamee</text>
				<text class="user-vip">VIP1</text>
			</view>
			<view class="user-r">
				<uni-icons type="arrowright" size="20"></uni-icons>
			</view>
		</navigator>
		<!-- 会员 -->
		<navigator url="" hover-class="nhover" class="vip">
			<view class="vip-le">
				<image class="vipicon" src="/static/icon/icon04.png" mode="aspectFit"></image>
				<text class="viptit">会员</text>
			</view>
			<view class="vip-ri">
				<text class="vipinfo">首开仅9元</text>
				<text class="vipbtn">立即前往</text>
			</view>
		</navigator>
		<!-- 菜单项目 -->
		<view class="mlist">
			<navigator url="/pages/readhis/index" class="mitem" hover-class="nhover">
				<text class="mtxt">阅读历史</text>
				<view class="mr">
					<uni-icons type="arrowright" size="20"></uni-icons>
				</view>
			</navigator>
			<navigator url="" class="mhis" hover-class="nhover">
				<image src="/static/temp/ls01.jpg" mode="aspectFill" class="mhisimg"></image>
				<view class="mhisinfo">
					<text class="mhistit">诛心之罪诛心之罪诛心之罪诛心之罪</text>
					<text class="mhisdec">2话 / 236话</text>
				</view>
			</navigator>
			<navigator url="" class="mitem" hover-class="nhover">
				<text class="mtxt">我的消息</text>
				<view class="mr">
					<uni-badge text="1" type="error"></uni-badge>
					<uni-icons type="arrowright" size="20"></uni-icons>
				</view>
			</navigator>
			<navigator url="" class="mitem" hover-class="nhover">
				<text class="mtxt">我的设置</text>
				<view class="mr">
					<uni-icons type="arrowright" size="20"></uni-icons>
				</view>
			</navigator>
			<navigator url="" class="mitem" hover-class="nhover">
				<text class="mtxt">帮助与反馈</text>
				<view class="mr">
					<uni-badge text="1" :is-dot="true" type="error"></uni-badge>
					<uni-icons type="arrowright" size="20"></uni-icons>
				</view>
			</navigator>
		</view>
		<!-- 退出登录 -->
		<view class="logout">
			<button class="logoutbtn">退出登录</button>
		</view>
	</view>
</template>

<script>
	export default {
		data() {
			return {}
		},
		methods: {},
		onLoad() {

		},
		onUnload() {

		}
	}
</script>

<style lang="scss" scoped>
	.menus {
		padding: 100rpx 30rpx 30rpx;
		box-sizing: border-box;
	}

	// 用户
	.user {
		display: flex;
		justify-content: space-between;
		align-items: center;
	}

	.user-l {
		align-items: center;
		display: flex;
	}

	.user-img {
		border-radius: 50%;
		border: 2px solid #000000;
		width: 36px;
		height: 36px;
		overflow: hidden;
	}

	.uimg {
		width: 100%;
		height: 100%;
		border-radius: 50%;
	}

	.user-name {
		display: block;
		font-size: 32rpx;
		color: #000;
		font-weight: 100;
		max-width: 190rpx;
		padding: 0 15rpx;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
	}

	.user-vip {
		display: block;
		padding: 5rpx 15rpx;
		border-radius: 100px;
		background-image: linear-gradient(to right, #fede50, #a27efc);
		font-size: 12px;
		color: #372c5a;
		font-weight: normal;
	}

	// 会员
	.vip {
		margin-top: 30rpx;
		display: flex;
		align-items: center;
		justify-content: space-between;
		padding: 15rpx 20rpx;
		border-radius: 12rpx 12rpx 0 0;
		background-image: linear-gradient(to right, #000000, #443d5e, #000000);
	}

	.vip-le {
		display: flex;
		align-items: center;
	}

	.vipicon {
		width: 23rpx;
		height: 24rpx;
	}

	.viptit {
		font-size: 14px;
		color: #fc0;
		margin-left: 10rpx;
	}

	.vip-ri {
		align-items: center;
	}

	.vipinfo {
		font-size: 12px;
		color: #fc0;
		font-weight: 100;
	}

	.vipbtn {
		margin-left: 10rpx;
		background-color: #ffcc00;
		padding: 5rpx 15rpx;
		border-radius: 100px;
		font-size: 14px;
		color: #282828;
	}

	.mlist {
		margin-top: 15rpx;
	}

	.mitem {
		display: flex;
		justify-content: space-between;
		align-items: center;
		padding: 30rpx 0;
		border-bottom-color: #eeeeee;
		border-bottom-width: 1px;
		border-bottom-style: solid;
	}

	.mtxt {
		font-size: 14px;
		color: #000;
	}

	.mr {
		display: flex;
		align-items: center;
	}

	//历史
	.mhis {
		display: flex;
		align-items: center;
		padding: 15rpx;
		border-radius: 15rpx;
		background-color: #f2f2f2;
	}

	.mhisimg {
		width: 90rpx;
		height: 90rpx;
		border-radius: 15rpx;
		margin-right: 15rpx;
	}

	.mhisinfo {
		width: 70%;
	}

	.mhistit {
		font-weight: 100;
		font-size: 18px;
		color: #000;
		overflow: hidden;
		text-overflow: ellipsis;
		white-space: nowrap;
		display: block;
	}

	.mhisdec {
		font-weight: 100;
		font-size: 14px;
		color: #666;
		margin-top: 10rpx;
		display: block;
	}

	// 退出
	.logout {
		margin-top: 60rpx;
	}

	.logoutbtn {
		font-size: 14px;
		color: #000;
		background-color: #f2f2f2;
		border-radius: 1000px;
		text-align: center;
		border: 1px solid #dddddd;

		&::after {
			display: none;
		}

		&:active {
			opacity: .8;
		}
	}
</style>
