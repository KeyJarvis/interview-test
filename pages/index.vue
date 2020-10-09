<template>
  <div :class="flag ? 'app' : ''">
    <button
      class="btn"
      @click="eject"
    >
      <p>Click Me</p>
    </button>
    <div
      class="model"
      v-show="flag"
    >
      <div class="model-title">
        <p>这是一个标题</p>
      </div>
      <div class="model-content">
        <p>{{content}}</p>
      </div>
      <div class="model-button">
        <button
          class="btn-cancal"
          @click="cancel"
        >
          <p>取消</p>
        </button>
        <button
          class="btn-confirm"
          @click="confirm"
        >
          <p>确定</p>
        </button>
      </div>
    </div>
    <div
      class="tips"
      v-show="isShow"
    >{{message}}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      flag: false,
      isShow: false,
      message: '',
      content:
        'Nuxt.js 是一个基于 Vue.js 的通用应用框架。通过对客户端/服务端基础架构的抽象组织，Nuxt.js 主要关注的是应用的 UI 渲染。我们的目标是创建一个灵活的应用框架，你可以基于它初始化新项目的基础结构代码，或者在已有 Node.js 项目中使用 Nuxt.js。'
    }
  },
  methods: {
    // 弹出
    eject() {
      this.flag = true
    },
    // 取消
    cancel() {
      this.flag = false
      this.message = '你取消了该操作！'
      this.isShow = true
      setTimeout(() => {
        this.isShow = false
      }, 2000)
    },
    // 确认
    confirm() {
      this.flag = false
      this.message = '你确认了该操作！'
      this.isShow = true
      setTimeout(() => {
        this.isShow = false
      }, 2000)
    }
  }
}
</script>

<style lang="scss">
.app {
  position: fixed;
  width: 100%;
  height: 100%;
  top: 0;
  left: 0;
  background: rgba(0, 0, 0, 0.5);
}
.btn {
  background: #3498db;
  width: 180px;
  padding: 16px 0;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translateX(-50%) translateY(-50%);
  border-radius: 3px;
  outline: none;
  border: none;
  &:hover {
    background: #2d8bca;
  }
  p {
    color: #f0f0f0;
    font-weight: 600;
    font-size: 16px;
  }
}
.model {
  width: 600px;
  position: absolute;
  top: 50%;
  left: 50%;
  z-index: 9999;
  margin: -150px 0 0 -300px;
  background-color: #fff;
  border-radius: 9px;
  border: 1px solid #ccc;
  animation: showModel 0.3s;
  -webkit-animation: showModel 0.3s;
}
.model-title {
  width: 100%;
  height: 48px;
  position: relative;
  // border-bottom: 1px solid grey;
  p {
    margin-left: 20px;
    line-height: 48px;
  }
  &:after {
    content: ' ';
    width: 96%;
    height: 0.12rem;
    background: #3498db;
    position: absolute;
    bottom: -0.1rem;
    left: 50%;
    transform: translateX(-50%);
  }
}
.model-content {
  padding-top: 20px;
  width: 90%;
  margin: 0 auto;
}
.model-button {
  width: 100%;
  margin: 20px 0px 20px 0px;
  text-align: right;
  padding-right: 10px;
  .btn-confirm {
    background: #3498db;
    width: 90px;
    padding: 10px 0;
    border-radius: 3px;
    outline: none;
    border: none;
    &:hover {
      background: #2d8bca;
    }
    p {
      color: #f0f0f0;
      font-weight: 600;
      font-size: 16px;
      letter-spacing: 9px;
      padding-left: 9px;
    }
  }
  .btn-cancal {
    background: #d5622d;
    width: 90px;
    padding: 10px 0;
    border-radius: 3px;
    outline: none;
    border: none;
    &:hover {
      background: #fa7233;
    }
    p {
      color: #f0f0f0;
      font-weight: 600;
      font-size: 16px;
      letter-spacing: 9px;
      text-align: center;
      padding-left: 9px;
    }
  }
}

.tips {
  margin: 0 auto;
  top: 80px;
  position: relative;
  background: #73acd1;
  border-radius: 4px;
  width: 180px;
  height: 36px;
  line-height: 36px;
  color: #fff;
  text-align: center;
  animation: showModel 0.3s;
  -webkit-animation: showModel 0.3s;
}
@keyframes showModel {
  0% {
    -webkit-transform: translate3d(0, -20%, 0);
    -webkit-transform: translate3d(0, -20%, 0);
    transform: translate3d(0, -20%, 0);
    transform: translate3d(0, -20%, 0);
    opacity: 0;
  }
  100% {
    -webkit-transform: none;
    transform: none;
    opacity: 1;
  }
}

@-webkit-keyframes showModel {
  0% {
    -webkit-transform: translate3d(0, -20%, 0);
    opacity: 0;
  }
  100% {
    -webkit-transform: none;
    opacity: 1;
  }
}

@keyframes hiddenModel {
  0% {
    transform: skew(40deg);
    opacity: 1;
  }
  50% {
    transform: skew(-40deg);
    opacity: 0.2;
  }
  100% {
    transform: skew(0deg);
    opacity: 0;
  }
}
</style>