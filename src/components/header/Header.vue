<template>
  <div class="header">
   <div class="content-wrap">
     <div class="avatar">
       <img width="64px" height="64px" :src="seller.avatar"/>
     </div>
     <div class="content">
       <div class="title">
         <span class="brand"></span>
         <span class="name">{{ seller.name }}</span>
       </div>
       <div class="description">
         {{ seller.description }}/{{ seller.deliveryTime }}分钟送达
       </div>
       <div class="support" v-if="seller.supports">
          <span class="icon" :class="classMap[seller.supports[0].type]"></span>
          <span class="text">{{ seller.supports[0].description }}</span>
       </div>
     </div>
     <div v-if="seller.supports" class="support-count">
       <span class="count">{{ seller.supports.length }}个</span>
       <i class="icon-keyboard_arrow_right"></i>
     </div>
   </div>
   <div class="bulletin-wrap">
     <span class="bulletin-title"></span><span class="bulletin-text">{{ seller.bulletin }}</span>
     <i class="icon-keyboard_arrow_right"></i>
   </div>
  </div>
</template>

<script>
  export default{
    name:'Header',
    data(){
      return {
        classMap:[],
      }
    },
    props: {
      seller: {
          type: Object,
      }
    },
    created() {
      this.classMap=['decrease','discount','specail','invoice','guarantee']
    }
  }
</script>

<style lang="less">
  @import '../../common/css/mixmin.less';
  .header{
    background-color:#999;
    color:#fff;
    .content-wrap{
      position: relative;
      padding: 24px 12px  18px  24px;
      /* 解决缝隙问题*/
      font-size: 0;
      .avatar{
        display: inline-block;
        vertical-align: top;
        img{
          border-radius: 2px;;
        }
      }
      .content{
        display: inline-block;
        margin-left: 14px;
        font-size: 14px;
        .title{
          margin:2px 0px 8px 0px;
          .brand{
            vertical-align: top;
            display: inline-block;
            width: 30px;
            height: 18px;
            .bg-image('brand');
            background-size: 30px  18px;
            background-repeat: no-repeat;
          }
          .name{
            margin-left: 6px;
            font-size:16px;
            font-weight: bold;
            line-height: 18px;
          }
        }
        .description{
          margin-bottom: 10px;
          line-height: 12px;
          font-size: 12px;
        }
        .support{
          .icon{
            display: inline-block;
            vertical-align: middle;
            width: 12px;
            height: 12px;
            margin-right: 4px;
            background-size: 12px 12px;
            background-repeat: no-repeat;
            &.decrease{
              .bg-image('decrease_1');
            }
            &.discount{
              .bg-image('discount_1');
            }
            &.guarantee{
              .bg-image('guarantee_1')
            }
            &.invoice{
              .bg-image('invoice_1');
            }
            &.specail{
              .bg-image('special_1')
            }
          }
          .text{
            line-height: 12px;
            font-size: 12px;
          }
        }
      }
      .support-count{
        position: absolute;
        right: 12px;
        bottom: 14px;
        padding: 0px 8px;
        height: 24px;
        line-height: 24px;
        border-radius: 14px;
        background-color:rgba(0,0,0,0.2);
        text-align: center;
        .count{
          font-size: 10px;
          vertical-align: top;
        }
        .icon-keyboard_arrow_right{
          margin-left: 2px;
          line-height: 24px;
          font-size:10px;
        }
      }
    }
    .bulletin-wrap{
      position: relative;
      height: 28px;
      line-height: 28px;
      padding: 0px 24px 0px 12px;
      white-space: nowrap;
      overflow: hidden;
      text-overflow: ellipsis;
      background-color:rgba(7,17,27,0.2);
      .bulletin-title{
        display: inline-block;
        vertical-align: top;
        margin-top: 8px;
        width: 22px;
        height: 12px;
        .bg-image('bulletin');
        background-size: 22px 12px;
        background-repeat: no-repeat;
      }
      .bulletin-text{
        font-size: 10px;
        margin: 0px 4px;
        vertical-align: top;
      }
      .icon-keyboard_arrow_right{
        position: absolute;
        font-size: 10px;
        right: 12px;
        top:8px;
      }
    }
  }
</style>
