<template>
	<div class="goods-item">
		<img :src="goodsItem.show.img" alt=""/>
		
		<div class="goods-info">
			<p>{{goodsItem.title}}</p>
			<span class="price">{{goodsItem.price}}元</span>
			<span class="collect">{{goodsItem.cfav}}</span>
		</div>
	</div>
</template>

<script>
	export default{
		props:{
			goodsItem:{
				type: Object,
				default(){
					return []
				}
			}
		}
	}
</script>

<style scoped>
  .goods-item{
		width: 48%;
    padding-bottom:40px;
		position: relative;		/*/子绝父相定位*/
  }
  .goods-item img{
    width:100%;
		border-radius: 5px;
  }
	.goods-info{
		font-size: 12px;
		position: absolute;
		bottom: 5px;
		left: 0;
		right: 0;
		overflow: hidden;
		text-align: center;
	}
  .goods-info p{
    margin-bottom: 3px;
		text-overflow: ellipsis;
		overflow: hidden;
		white-space: nowrap;
  }
	.goods-info .price{
		margin-right: 20px;
		color: var(--color-high-text);
		margin-bottom: 20px;
	}
	.goods-info .collect{
		position: relative;
	}
	.goods-info .collect::before{
		content: '';
		position: absolute;
		left: -15px;
		top: -1px;
		width: 14px;
		height: 14px;
		background: url('@/assets/img/common/collect.svg') 0 0/14px 14px;
	}
</style>