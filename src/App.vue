<template>
  <div id="app">
    <v-header :seller="seller"></v-header>
    <div class="tabs">
      <div class="tabItem"><router-link :to="{path:'/goods'}">商品</router-link></div>
      <div class="tabItem"><router-link :to="{path:'/ratings'}">评价</router-link></div>
      <div class="tabItem"><router-link :to="{path:'/seller'}">商家</router-link></div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
  const ERR_OK = 0;
  import Header from './components/header/Header'
export default {
  name: 'App',
  data(){
    return {
      title:'主组件',
      seller:{}
    }
  },
  components:{
    'v-header':Header
  },
  created() {
    this.$http.get('/api/seller').then(res=>{

      if(res.body.errno === ERR_OK){
        this.seller = res.body.data;
      }
    },req=>{

    });
  }
}
</script>

<style lang="less">
@import './common/css/mixmin.less';
*{
  margin:0px;
  padding:0px;
}
a{
  color:#333;
  text-decoration: none;
}
.tabs{
  display: flex;
  width:100%;
  height: 40px;
  line-height: 40px;
  .border-1px(#eaeaea);
  .tabItem{
    flex: 1;
    text-align: center;
    a{
      display: block;
      font-size:14px;
      &.router-link-active{
        color:#ff0000;
      }
    }
  }
}
</style>
