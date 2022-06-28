<template>
	<div class="tab-bar-item" @click="itemClick">
		<div v-if="!isAtive"><slot name="item-icon"></slot></div>
		<div v-else><slot name="item-icon-active"></slot></div>
		<div :style="activestyle"><slot name="item-text"></slot></div>
	</div>
</template>

<script>
	export default {
		props:{
			path: String,
			activeColor:{
				type: String,
				default:'blue'
			}
		},
		data() {
			return {
				//isAtive: true
			}
		},
		computed:{
			isAtive(){
				//return this.$route.path.indexOf(this.path) !== -1
				return this.$route.path == this.path
			},
			activestyle(){
				return this.isAtive ? {color: this.activeColor} : {}
			}
		},
		methods: {
			itemClick(){
				//console.log("itemClick")
				this.$router.replace(this.path);
			}
		}
	}
</script>

<style>
	.tab-bar-item{
	flex: 1;
	text-align: center;
	height: 49px;
	}
	
	.tab-bar-item img{
	  width: 24px;
	  height: 24px;
	  margin-top: 3px;
	  /* 去除中间空隙 */
	  vertical-align: middle;
		}
/* 		.active{
			color: red;
		} */
</style>