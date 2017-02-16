<template>
  <div class="header">
    <div class="content-wrapper">
      <div class="avatar">
        <img width="64" height="64" :src="seller.avatar">
      </div>
      <div class="content">
        <div class="title">
          <span class="brand"></span>
          <span class="name">{{seller.name}}</span>
        </div>
        <div class="description">
          {{seller.description}}/{{seller.deliveryTime}}分钟送达
        </div>
        <div v-if="seller.supports" class="support">
          <span class="icon" :class="classMap[seller.supports[0].type]"></span>
          <span class="text">{{seller.supports[0].description}}</span>
        </div>
      </div>
      <div v-if="seller.supports" class="support-count">
        <span class="count">{{seller.supports.length}}个</span>
        <i class="icon-keyboard_arrow_right"></i>
      </div>
    </div>
    <div class="bulletin-wrapper">
      <span class="bulletin-title"></span><span class="bulletin-text">{{seller.bulletin}}</span>
      <i class="icon-keyboard_arrow_right"></i>
    </div>
    <div class="background">
      <img :src="seller.avatar" width="100%" height="100%">
    </div>
  </div>
</template>

<script>
  export default {
    props: {
      seller: {
        type: Object
      }
    },
    created () {
      this.classMap = ['decrease', 'discount', 'special', 'invoice', 'guarantee']
    }
  }
</script>

<style lang="stylus" rel="stylesheet/stylus">
  @import "../../common/stylus/mixin.styl"
  .header
    position relative
    background rgba(7,17,27,0.5)
    color #fff
    .content-wrapper
      padding 24px 16px 18px 24px
      font-size 0px
      position relative
      .avatar
        display inline-block
        vertical-align top
        img
          border-radius 2px
      .content
        margin-left 16px
        display inline-block
        .title
          margin 2px 0 8px 0
          .brand
            display inline-block
            vertical-align top
            width 30px
            height 18px
            bg-img ('brand')
            background-size 30px 18px
            background-repeat no-repeat
          .name
            font-size 16px
            font-weight bold
            line-height 18px
            margin-left 6px
        .description
          margin-bottom 10px
          font-size 12px
          line-height 12px
        .support
          .icon
            width 12px
            height 12px
            display inline-block
            margin-right 4px
            background-size 12px 12px
            vertical-align top
            background-repeat no-repeat
            &.decrease
              bg-img ('decrease_1')
            &.discount
              bg-img ('discount_1')
            &.invoice
              bg-img ('invoice_1')
            &.guarantee
              bg-img ('guarantee_1')
            &.special
              bg-img ('special_1')
          .text
            font-size 12px
            line-height 12px
      .support-count
        position absolute
        right 12px
        bottom 14px
        padding 0 8px
        height 24px
        line-height 24px
        border-radius 14px
        background rgba(0,0,0,0.2)
        text-align center
        .count
          font-size 10px
          vertical-align top
        .icon-keyboard_arrow_right
          font-size 10px
          line-height 24px
          margin-left 2px
    .bulletin-wrapper
      position relative
      height 28px
      line-height 28px
      padding 0 22px 0 12px
      white-space nowrap
      overflow hidden
      text-overflow ellipsis
      background rgba(7,17,27,0.2)
      .bulletin-title
        display inline-block
        vertical-align top
        margin-top 9px
        width 22px
        height 12px
        bg-img ('bulletin')
        background-size 22px 12px
        background-repeat no-repeat
      .bulletin-text
        vertical-align top
        font-size 10px
        margin 0 4px
      .icon-keyboard_arrow_right
        font-size 10px
        position absolute
        top 8px
        right 12px
    .background
      position absolute
      top 0
      left 0
      width 100%
      height 100%
      z-index -1
      filter blur(10px)
</style>
