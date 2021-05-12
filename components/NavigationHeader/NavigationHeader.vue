<template>
	<!-- 公用头部 -->
	<div class="content" :style="headerStyle">
		<div class="status_bar" :style="statusBarStyle"></div>
		<div class="header">
			<slot name="left">
				<div class="c left_arrow"><text>左</text></div>
			</slot>

			<slot name="center">
				<div class="c center_text"><text>微信</text></div>
			</slot>

			<slot name="right">
				<div class="c options">
					<div class="o"><text>右</text></div>
				</div>
			</slot>
		</div>
	</div>
</template>

<script>
	// 工具类
	import {
		UniApi
	} from '@/utils/Utils';

	let t;

	export default {
		name: "NavigationHeader",
		data() {
			return {
				headerStyle: {}, // 盒子样式

				statusBarStyle: {}, // 状态栏样式
			};
		},

		created() {
			t = this;
			t.init()
		},

		methods: {
				// 初始化高度
			init() {
				const {
					windowWidth,
					statusBarHeight
				} = UniApi.getSystem()
				t.headerStyle.height = `${UniApi.calcRpx(statusBarHeight) + 120}rpx`;
				t.statusBarStyle.height = `${statusBarHeight}px`
			},
		},
	}
</script>

<style lang="scss">
	.content {
		flex-direction: column;
		background-color: skyblue;
		// 头部内容
		.header{
			flex-direction: row;
			align-items: center;
			height: 120rpx;
			background-color: pink;
		
			// 左中右
			.c{
				flex :1;
				align-items: center;
				justify-content: center;
			}
		}
	}
</style>
