<template>
	<view class="booklist" :class="{booklist2:col==2,booklist3:col==3}">
		<view class="item" v-for="(item,index) in [1,1,1,1,1,1]">
			<view class="booksign"></view>
			<navigator class="itemhref" url="" hover-class="nhover">
				<book-item :rank="rank" :booknumse="booknumse"></book-item>
			</navigator>
		</view>
	</view>
</template>

<script>
	export default {
		props: {
			col: {
				type: [String, Number],
				default: 3
			},
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
	.booklist {
		display: flex;
		flex-wrap: wrap;

		.item {
			position: relative;
			margin-bottom: 20rpx;
		}

		&.booklist3 {
			.item {
				width: 32%;
				margin-right: 2%;

				&:nth-child(3n) {
					margin-right: 0;
				}

				&:nth-last-child(-n+3) {
					margin-bottom: 0;
				}
			}

		}

		&.booklist2 {
			justify-content: space-between;

			.item {
				position: relative;
				width: 49%;
				margin-bottom: 20rpx;

				&:nth-last-child(-n+2) {
					margin-bottom: 0;
				}
			}
		}
	}
</style>
