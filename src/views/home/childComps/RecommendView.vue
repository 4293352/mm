<template>
	<div class="recommend">
		<div v-for="item in recommends">
			<a>
				<img :src="item.image" alt=""/>
				<div>{{item.title}}</div>
			</a>
		</div>
	</div>
</template>

<script>
	export default {
		props: {
			recommends: {
				type: Array,
				default(){
					return []
				}
			}
		}
	}
</script>

<style>
	.recommend{
		display: flex;
		width: 100%;
		text-align: center;
		margin: 0 auto;
		font-size: 12px;
		padding: 10px 0 20px;
	}
 	.recommend-item {
		flex: 1;
	}
	.recommend img{
		width: 70px;
		height: 70px;
		margin-bottom: 10px;
	} 
</style>