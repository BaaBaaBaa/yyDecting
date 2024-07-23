<template>
	<view class="inputs">
	
		<view class="detection-line">
			<view class="label">
				孵育时间：
			</view>
			<input class="input" type="number" placeholder="" />
			<view class="unit">
				min
			</view>
		</view>
		<view class="detection-line">
			<view class="label">
				孵育温度：
			</view>
			<input class="input" type="number" placeholder="" />
			<view class="unit">
				℃
			</view>
		</view>
		<view class="detection-line">
			<view class="label">
				采样间隔：
			</view>
			<input class="input" type="number" placeholder="" />
			<view class="unit">
				S
			</view>
		</view>
	</view>
	<view class="bottom">
		<view class="save-btn">
			保存设置
		</view>
		<view class="p1">
			项目配置版本: v1.0
		</view>
		<view class="p2">
			阳参配置版本: v1.0
		</view>
	</view>
</template>

<script setup>
	
</script>

<style lang="scss" scoped>
	.inputs {
		
	}
	.detection-line {
		width: 256px;
		height: 68px;
		font-size: 18px;
		display: flex;
		align-items: center;
	}
	
	.input {
		width: 106px;
		height: 28px;
		border-radius: 3px;
		border: 1px solid #cfcfcf;
		margin-left: 16px
	}
	.unit {
		display: inline-block;
		flex: 1;
		text-align: right;
	}
	
	.bottom {
		width: 256px;
		margin-top: 10px;
		border-top: 1px #ededed solid;
		padding-top: 20px;
		display: flex;
		flex-direction: column;
		align-items: center;
	}
	.save-btn {
		width: 85px;
		height: 25px;
		display: flex;
		justify-content: center;
		align-items: center;
		background: #009ed6;
		color: #cdf4fb;
		border-radius: 3px;
		margin-bottom: 24px;
	}
	.p1, .p2 {
		font-size: 20px;
	}
	.p1 {
		margin-bottom: 10px;
	}
</style>