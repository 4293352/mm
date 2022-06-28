<template>
	<div class="nav-bar">
		<div class="left"><slot name="left"></slot></div>
		<div class="center"><slot name="center"></slot></div>
		<div class="right"><slot name="right"></slot></div>
	</div>
</template>

<script>
</script>

<style>
	.nav-bar{
		display: flex;
		height: 44px;
		line-height: 49px;
		text-align: center;
		box-shadow: 0 3px 1px rgba(100, 100, 100, 0.1);
	}
	.left, .right{
		width: 60px;
/* 		background-color: red;
 */	}
	.center{
		flex: 1;
		/* background-color: aqua; */
	}
</style>