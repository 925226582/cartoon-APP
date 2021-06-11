<script>
	import {
		mapState,
		mapMutations
	} from 'vuex'

	export default {
		onLaunch: function() {
			console.log('App Launch');
			let uniIdToken = uni.getStorageSync('uni_id_token')
			if (uniIdToken) {
				this.login(uni.getStorageSync('username'))
			}

			// #ifdef APP-PLUS
			// 一键登录预登陆，可以显著提高登录速度
			uni.preLogin({
				provider: 'univerify',
				success: (res) => {
					this.setUniverifyErrorMsg()
					this.setHideUniverify(false);
					console.log("preLogin success: ", res);
				},
				fail: (err) => {
					this.setUniverifyErrorMsg(err.errMsg)
					// 没有开通一键登录
					this.setHideUniverify(true);
					console.log("preLogin fail: ", err);
				}
			})
			// #endif
		},
		onShow: function() {
			console.log('App Show');
		},
		onHide: function() {
			console.log('App Hide');
		},
		methods: {
			...mapMutations(['login', 'setUniverifyErrorMsg', 'setHideUniverify']),
		}
	}
</script>

<style>
	/* 头条小程序需要把 iconfont 样式放到组件外 */
	@import "components/m-icon/m-icon.css";

	@font-face {
		font-family: "iconfont";
		/* Project id 2500771 */
		src: url('/static/iconfont.woff2?t=1623222703327') format('woff2'),
			url('/static/iconfont.woff?t=1623222703327') format('woff'),
			url('/static/iconfont.ttf?t=1623222703327') format('truetype');
	}

	view,
	text {
		font-weight: 100;
	}

	.iconfont {
		font-family: "iconfont" !important;
		font-size: 16px;
		font-style: normal;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
	}

	.icon-huiyuanquanyi:before {
		content: "\e739";
	}

	.icon-huiyuan:before {
		content: "\f5ff";
	}

	.icon-huiyuanzunxiang:before {
		content: "\eb80";
	}

	.icon-quanbuxiangyou-:before {
		content: "\e618";
	}

	.icon-quanbuxiangzuo-:before {
		content: "\e619";
	}

	.icon-paixu:before {
		content: "\e64f";
	}

	.icon-daoxu:before {
		content: "\e65a";
	}

	.icon-jindu:before {
		content: "\e7b0";
	}

	.icon-xiezuoxing:before {
		content: "\e7b3";
	}

	.icon-yueduye-yejianmoshi:before {
		content: "\e620";
	}

	.icon-rijianmoshixhdpi:before {
		content: "\e623";
	}

	.icon-mulu:before {
		content: "\e64e";
	}

	.icon-yejianmoshi:before {
		content: "\e6c1";
	}

	.icon-rijianmoshi:before {
		content: "\e6c7";
	}

	.icon-icon_commone_close:before {
		content: "\e610";
	}

	.icon-icon_more_up:before {
		content: "\e615";
	}

	.icon-icon_more_right:before {
		content: "\e614";
	}

	.icon-icon_more_down:before {
		content: "\e616";
	}

	.icon-icon_more_left:before {
		content: "\e617";
	}

	.icon-icon_commone_time:before {
		content: "\e611";
	}

	.icon-icon_commone_gouxuan:before {
		content: "\e607";
	}

	.icon-icon_commone_fabumian:before {
		content: "\e608";
	}

	.icon-icon_commone_kejianmian:before {
		content: "\e609";
	}

	.icon-icon_commone_fabu:before {
		content: "\e60a";
	}

	.icon-icon_commone_rili:before {
		content: "\e60b";
	}

	.icon-icon_commone_gouxuanmian:before {
		content: "\e60c";
	}

	.icon-icon_commone_pingjia:before {
		content: "\e60d";
	}

	.icon-icon_commone_rilimian:before {
		content: "\e60e";
	}

	.icon-icon_commone_pingjiamian:before {
		content: "\e60f";
	}

	.icon-Bookmark:before {
		content: "\e678";
	}

	.icon-Category:before {
		content: "\e679";
	}

	.icon-Chat:before {
		content: "\e67a";
	}

	.icon-Heart:before {
		content: "\e67b";
	}

	.icon-Home:before {
		content: "\e67c";
	}

	.icon-Paper:before {
		content: "\e67d";
	}

	.icon-Graph:before {
		content: "\e67e";
	}

	.icon-Notification:before {
		content: "\e67f";
	}

	.icon-Send:before {
		content: "\e680";
	}

	.icon-Password:before {
		content: "\e681";
	}

	.icon-Wallet:before {
		content: "\e682";
	}

	.icon-PaperDownload:before {
		content: "\e683";
	}

	.icon-PaperNegative:before {
		content: "\e684";
	}

	.icon-Swap:before {
		content: "\e685";
	}

	.icon-PaperPlus:before {
		content: "\e686";
	}

	.icon-PaperFail:before {
		content: "\e687";
	}

	.icon-Search:before {
		content: "\e688";
	}

	.icon-PaperUpload:before {
		content: "\e689";
	}

	.icon-Work:before {
		content: "\e68a";
	}

	.icon-Folder:before {
		content: "\e68b";
	}



	/*每个页面公共css */
	page {
		min-height: 100%;
		display: flex;
		font-size: 14px;
	}

	input,
	textarea,
	button {
		font-size: 14px;
	}

	/* #ifdef MP-BAIDU */
	page {
		width: 100%;
		height: 100%;
		display: block;
	}

	swan-template {
		width: 100%;
		min-height: 100%;
		display: flex;
	}

	/* 原生组件模式下需要注意组件外部样式 */
	custom-component {
		width: 100%;
		min-height: 100%;
		display: flex;
	}

	/* #endif */

	/* #ifdef MP-ALIPAY */
	page {
		min-height: 100vh;
	}

	/* #endif */

	/* 原生组件模式下需要注意组件外部样式 */
	m-input {
		width: 100%;
		/* min-height: 100%; */
		display: flex;
		flex: 1;
	}

	.content {
		display: flex;
		flex: 1;
		flex-direction: column;
		background-color: #efeff4;
		padding: 10px;
	}

	.input-group {
		background-color: #ffffff;
		margin-top: 20px;
		position: relative;
	}

	.input-group::before {
		position: absolute;
		right: 0;
		top: 0;
		left: 0;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}

	.input-group::after {
		position: absolute;
		right: 0;
		bottom: 0;
		left: 0;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}

	.input-row {
		display: flex;
		flex-direction: row;
		position: relative;
		/* font-size: 18px; */
		height: 40px;
		line-height: 40px;
	}

	.input-row .title {
		width: 70px;
		padding-left: 15px;
	}

	.input-row.border::after {
		position: absolute;
		right: 0;
		bottom: 0;
		left: 8px;
		height: 1px;
		content: '';
		-webkit-transform: scaleY(.5);
		transform: scaleY(.5);
		background-color: #c8c7cc;
	}

	.btn-row {
		margin-top: 25px;
		padding: 10px;
	}

	button.primary {
		background-color: #0faeff;
	}

	.wcont {
		padding: 0 30rpx;
		box-sizing: border-box;
	}

	.nhover {
		opacity: .8;
	}
</style>
