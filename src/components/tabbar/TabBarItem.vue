<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if="!isActive"><slot name="item-icon"></slot></div>
    <div v-else><slot name="item-icon-active"></slot></div>
    <div :style="activeStyle"><slot name="item-text"></slot></div>

<!--    <img src="../../assets/img/tabbar/home.svg"/>
    <div class="tab-bar-item">首页</div> -->
  </div>
<!--  <div id="app">
    <tab-bar>
        <div class="text-bar-item">
          <img src="../../assets/img/tabbar/home.svg"/>
          <div>首页</div>
        </div>
        <div class="text-bar-item">
          <img src="../../assets/img/tabbar/home.svg"/>
          <div>分类</div>
        </div>
        <div class="text-bar-item">
          <img src="../../assets/img/tabbar/home.svg"/>
          <div>购物车</div>
        </div>
        <div class="text-bar-item">
          <img src="../../assets/img/tabbar/home.svg"/>
          <div>我的</div>
        </div>
    </tab-bar>
  </div>-->
</template>

<script>
  export default{
    props:{
      path:String,
      activeColor:{
        type:String,
        default:'red'
      }
    },
    data(){
      return{
        //isActive:true,
        //isActive:false
      }
    },
    computed:{
      isActive(){
        //  /home -> item1(/home) = true
        //  /home -> item1(/category) = false
        //  /home -> item1(/cart) = true
        //  /home - >item1(/profile) = true
        //return this.$route.path.indexOf(this.path) !== -1
        return this.$route.path == this.path
      },
      activeStyle(){
        return this.isActive ? {color: this.activeColor} : {}
      }
    },
    methods:{
      itemClick(){
        //console.log('itemClick');
        this.$router.replace(this.path)
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
    height: 24;
    margin-top: 3px;
    /* 去除中间空隙 */
    vertical-align: middle;
  }
/*  .active{
    color: red;
  } */
</style>
