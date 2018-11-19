<template>
  <div v-show="visible" class="hlj-modal" :class="{show: visible}">
    <div class="hlj-modal-content">
      <div v-if="title" class="hlj-modal-header">
        {{title}}
      </div>
      <div class="hlj-modal-body" :class="{'hlj-modal-body_no-header': !title}">
        {{content}}
      </div>
      <div class="hlj-modal-footer">
        <div v-if="showCancel" class="hlj-modal-btn hlj-modal-cancle">
          <a @click="handleBtnClick" :style="{color: cancelColor}">{{cancelText}}</a>
        </div>
        <div class="hlj-modal-btn hlj-modal-comform" @click="handleBtnClick">
          <a @click="handleBtnConfirm" :style="{color: confirmColor}">{{confirmText}}</a>
          <button
            v-if="openType === 'getPhoneNumber'"
            open-type="getPhoneNumber"
            class="hlj-modal-auth"
            @getphonenumber="handleAuthBtnChange"/>
          <button
            v-if="openType === 'contact'"
            open-type="contact"
            class="hlj-modal-auth"
            @contact="handleAuthBtnChange"/>
          <button
            v-if="openType === 'share'"
            open-type="share"
            class="hlj-modal-auth"/>
          <button
            v-if="openType === 'getUserInfo'"
            open-type="getUserInfo"
            class="hlj-modal-auth"
            @getuserinfo="handleAuthBtnChange"/>
          <button
            v-if="openType === 'openSetting'"
            open-type="openSetting"
            class="hlj-modal-auth"
            @opensetting="handleAuthBtnChange"/>
        </div>
      </div>
    </div>
    <div class="hlj-modal-mark" @click="$emit('close')"></div>
  </div>
</template>

<script>
  export default {
    name: 'hlj-modal',
    props: {
      visible: Boolean,
      title: String,
      content: String,
      openType: String,
      showCancel: {
        type: Boolean,
        default: true
      },
      cancelText: {
        type: String,
        default: '取消'
      },
      cancelColor: {
        type: String,
        default: '#353535'
      },
      confirmText: {
        type: String,
        default: '确定'
      },
      confirmColor: {
        type: String,
        default: '#3CC51F'
      }
    },
    data () {
      return {
      }
    },

    methods: {
      handleBtnClick () {
        this.$emit('close')
      },
      handleBtnConfirm (e) {
        if (this.openType) return
        this.$emit('confirm', e)
      },
      handleAuthBtnChange (e) {
        this.$emit('confirm', e)
      }
    }
  }
</script>

<style lang="less">
  .hlj-modal {
    opacity: 0;
    transition: opacity .2s linear 0s;
    &.show {
      opacity: 1;
    }
    .hlj-modal-header {
      line-height: 28px;
      padding: 20px 25px 8px;
      font-size: 18px;
    }
    .hlj-modal-content {
      position: fixed;
      top: 50%;
      left: 50%;
      width: 80%;
      max-width: 300px;
      transform: translate(-50%, -50%);
      z-index: 9999;
      border-radius: 3px;
      background: #fff;
      text-align: center;
      .hlj-modal-body {
        padding: 0 24px 12px;
        border-bottom: 1px solid #D5D5D6;
        font-size: 15px;
        color: #808080;
        &_no-header {
          padding: 40px 20px 25px;
        }
      }
      .hlj-modal-footer {
        position: relative;
        line-height: 48px;
        font-size: 18px;
        display: flex;
        .hlj-modal-btn {
          display: block;
          -webkit-flex: 1;
          flex: 1;
          text-decoration: none;
          -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
          position: relative;
          &::after {
            content: ' ';
            position: absolute;
            left: 0;
            top: 0;
            width: 1px;
            bottom: 0;
            border-left: .5px solid #D5D5D6;
            color: #D5D5D6;
          }
          &:first-child::after {
            border: none;
          }
        }
        .hlj-modal-cancle {
          color: #353535;
        }
        .hlj-modal-comform {
          position: relative;
          color: #09BB07;
        }
        .hlj-modal-auth {
          position:absolute;
          width: 100%;
          height: 50px;
          top: 0;
          opacity: 0;
        }
      }
    }
    .hlj-modal-mark {
      position: fixed;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
      z-index: 9998;
      background: rgba(0, 0, 0, 0.6);
    }
  }
</style>
