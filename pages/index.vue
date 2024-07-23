<template>
	<view class="container">
		<view class="test"></view>
		<view class="header">
			<view class="header-left">
				<view class="logo with-border-right"></view>
				<view class="nav-list">
					<view class="nav-item with-border-right" v-for="item in navList" :key="item.index"
						:class="{ active: item.index === activeIndex }" @click="handleNavClick(item.index)"
					>
						<image class="nav-icon" :src="item.icon" mode=""></image>
						<view class="nav-item-text">
							{{ item.text }}
						</view>
					</view>
					
				</view>
			</view>
			<view class="header-right">
				<view class="date">
					{{ dateFormatText }}
				</view>
				<view class="temperature">
					{{ 42 }} ℃
				</view>
			</view>
		</view>
		
		<view class="main">
			<component :is="navList[activeIndex].component"></component>
		</view>
	</view>
</template>

<script setup>
import { computed, ref } from 'vue';
import Dectect from './dectect/index.vue';
import Search from './search/index.vue';
import Setting from './setting/index.vue';
	
	// 导航及切换
	const activeIndex = ref(0);
	const navList = [
		{
			index: 0,
			text: '检测',
			icon: '../static/header_nav/detect.png',
			component: Dectect
		},
		{
			index: 1,
			text: '查询',
			icon: '../static/header_nav/search.png',
			component: Search
		},
		{
			index: 2,
			text: '设置',
			icon: '../static/header_nav/setting.png',
			component: Setting
		},
	];
	const handleNavClick = (index) => {
		if(index !== activeIndex.value) {
			activeIndex.value = index;
		}
	}
	
	// 左上时间和温度显示
	let now = ref(new Date());
	const intervalId = setInterval(() => {
		now.value = new Date();
	}, 1000);
	const dateFormatText = computed(() => {
		const date = now.value;
		let year=date.getFullYear();
		let month= date.getMonth()+1<10 ? "0"+(date.getMonth()+1) : date.getMonth()+1;
		let day=date.getDate()<10 ? "0"+date.getDate() : date.getDate();
		let hours=date.getHours()<10 ? "0"+date.getHours() : date.getHours();
		let minutes=date.getMinutes()<10 ? "0"+date.getMinutes() : date.getMinutes();
		let seconds=date.getSeconds()<10 ? "0"+date.getSeconds() : date.getSeconds();
		// 拼接
		return year+"-"+month+"-"+day+" "+hours+":"+minutes+":"+seconds;
	});
	
</script>

<style lang="scss" scoped>
	.container {
		
	}
	
	.header {
		width: 100vw;
		height: 86px;
		background: linear-gradient(to bottom, #61ae62, #8fccc7);
		display: flex;
		justify-content: space-between;
	}
	.with-border-right {
		height: 100%;
		border-right: 1px solid #f0fbf3;
	}
	.logo {
		width: 200px;
	}
	.nav-list, .header-left, .header-right {
		display: flex;
	}
	.nav-item {
		width: 178px;
		display: flex;
		justify-content: center;
		align-items: center;
		font-size: 24px;
		transition: .5s;
	}
	.nav-item.active {
		background: #708f87;
		.nav-item-text {
			color: #edf3f1;
		}
	}
	.nav-icon {
		width: 34px;
		height: 34px;
	}
	.nav-item-text {
		margin-left: 20px;
		color: #000;
	}
	.header-right {
		font-size: 24px;
		text-align: right;
		height: 86px;
		line-height: 86px;
	}
	.temperature {
		color: #fafdf9;
		margin: 0 12px;
	}
	
	.main {
		margin: 0 auto;
		height: 538px;
	}
	
	.test {
		display: none;
		width: 100rpx;
		height: 100rpx;
		background: red;
	}
</style>
