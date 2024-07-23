<template>
	<view class="setting-container">
		<view class="setting-nav-list">
			<view class="nav-item with-border-right" v-for="item in navList" :key="item.index"
				:class="{ active: item.index === activeIndex }" @click="handleNavClick(item.index)"
			>
				<image class="nav-icon" :src="item.index === activeIndex ? item.activeIcon : item.icon"></image>
				<view class="nav-item-text">
					{{ item.text }}
				</view>
			</view>
		</view>
		<view class="setting-main">
			<component :is="navList[activeIndex].component"></component>
		</view>
	</view>
</template>

<script setup>
import { ref } from 'vue';
import About from './about.vue';
import Application from './application.vue';
import Login from './login.vue';
import Detection from './detection.vue';

	// 左侧导航切换
	const activeIndex = ref(0);
	const navList = [
		{
			index: 0,
			text: '关于本机',
			icon: '../static/setting_nav/about.png',
			activeIcon: '../static/setting_nav/about_active.png',
			component: About
		},
		{
			index: 1,
			text: '应用设置',
			icon: '../static/setting_nav/application.png',
			activeIcon: '../static/setting_nav/application_active.png',
			component: Application
		},
		{
			index: 2,
			text: '登录设置',
			icon: '../static/setting_nav/login.png',
			activeIcon: '../static/setting_nav/login_active.png',
			component: Login
		},
		{
			index: 3,
			text: '检测设置',
			icon: '../static/setting_nav/detection.png',
			activeIcon: '../static/setting_nav/detection_active.png',
			component: Detection
		},
	];
	const handleNavClick = (index) => {
		if(index !== activeIndex.value) {
			activeIndex.value = index;
		}
	}
	
	
</script>

<style lang="scss">
	.setting-line-box {
		width: 256px;
		height: 60px;
		border-bottom: 1px #ededed solid;
		display: flex;
		justify-content: space-between;
		align-items: center;
		font-size: 18px;
		&:last-child {
			border-bottom: none;
		}
		
		.setting-btn {
			width: 60px;
			height: 28px;
			line-height: 28px;
			background: #009dd5;
			color: #fff;
			border-radius: 3px;
			text-align: center;
		}
	}
</style>
<style lang="scss" scoped>
	.setting-container {
		display: flex;
		height: 100%;
	}
	.setting-nav-list {
		width: 200px;
		height: calc(100vh - 86px);
		background: #e9e8e6;
	}
	.nav-item {
		width: 100%;
		height: 90px;
		display: flex;
		align-items: center;
		justify-content: center;
		font-size: 18px;
		color: #393738;
		// transition: .5s;
		&.active {
			color: #000;
			background: #d2e081;
		}
	}
	.nav-icon {
		width: 30px;
		height: 30px;
		margin-right: 24px;
		line-height: 30px;
	}
	
	.setting-main {
		flex: 1;
		display: flex;
		flex-direction: column;
		justify-content: center;
		align-items: center;
		padding-bottom: 40px;
	}
</style>