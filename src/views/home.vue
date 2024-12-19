<template>
  <div>
    <div class="item">
      <el-carousel :interval="5000" arrow="always">
        <el-carousel-item v-for="item in carouselList" :key="item">
          <div
            :style="{
              background: `url(${item}) center center / cover no-repeat`,
              height: '100%',
              width: '100%',
            }"
          ></div>
        </el-carousel-item>
      </el-carousel>
    </div>
    <div class="item page2" ref="targetElement" style="color: #fff">
      <div>
        <div style="margin-top: 20px;">
          <el-button
            type="primary"
            :loading="isDisabled"
            :disabled="isDisabled"
            @click="handleClick"
            >点击展示特效</el-button
          >
          <el-collapse-transition>
            <div v-show="show">
              <div class="transition-box">我是一个折叠特效演示</div>
            </div>
          </el-collapse-transition>
        </div>
        <div style="display: flex; margin-top: 20px;">
          <transition name="el-zoom-in-center">
            <div v-show="show" class="transition-box">中间缩放</div>
          </transition>

          <transition name="el-zoom-in-top">
            <div v-show="show" class="transition-box">向上缩放</div>
          </transition>

          <transition name="el-zoom-in-bottom">
            <div v-show="show" class="transition-box">向下缩放</div>
          </transition>
        </div>
        <div style="display: flex">
          <div class="element" v-show="show">
            <img
              src="../assets/images/chatglm.png"
              alt=""
              style="width: 6.03rem; height: 4.14rem"
            />
          </div>
          <div class="element2" v-show="show">
            <img
              src="../assets/images/chatglm.png"
              alt=""
              style="width: 6.03rem; height: 4.14rem"
            />
          </div>
        </div>
      </div>
    </div>
    <div class="item page3">
      <div class="scroll-container">
        <img
          src="../assets/images/1.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
        <img
          src="../assets/images/1.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
        <img
          src="../assets/images/1.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
      </div>
      <div class="scroll-container scroll-container2">
        <img
          src="../assets/images/2.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
        <img
          src="../assets/images/2.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
        <img
          src="../assets/images/2.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
      </div>
      <div class="scroll-container scroll-container3">
        <img
          src="../assets/images/3.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
        <img
          src="../assets/images/3.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
        <img
          src="../assets/images/3.png"
          class="scroll-image"
          alt="Scrolling Image"
        />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
  data() {
    return {
      isDisabled: false,
      show: false,
      carouselList: [
        require("../assets/images/tab1.png"),
        require("../assets/images/tab2.png"),
        require("../assets/images/tab3.jpg"),
        require("../assets/images/tab4.jpg"),
      ],
    };
  },
  mounted() {
    // 创建 Intersection Observer 实例
    const options = {
      root: null, // 使用视口作为容器
      threshold: 0.5, // 目标元素至少 50% 进入视口时触发
    };

    // 定义回调函数
    const callback = (entries, observer) => {
      entries.forEach((entry) => {
        if (entry.isIntersecting) {
          // 触发你的方法
          this.handleScrollInView();
        }
      });
    };

    // 创建观察者实例
    this.observer = new IntersectionObserver(callback, options);

    // 开始观察目标元素
    this.observer.observe(this.$refs.targetElement);
  },
  methods: {
    handleScrollInView() {
      // 这里是当元素进入视口时要触发的方法
      console.log("目标元素进入视口了！");
      if (!this.show) {
        this.show = !this.show;
      }
    },
    handleClick() {
      this.isDisabled = true;
      this.show = !this.show;
      setTimeout(() => {
        this.show = !this.show;
        this.isDisabled = false;
      }, 500);
    },
  },
  beforeDestroy() {
    // 在组件销毁之前停止观察
    if (this.observer) {
      this.observer.disconnect();
    }
  },
};
</script>

<style>
.item {
  height: 100vh;
  overflow: hidden;
}
.el-carousel--horizontal {
  height: 100% !important;
}
.el-carousel__container {
  height: 100% !important;
}
.el-carousel__arrow {
  background-color: transparent !important;
  font-size: 30px !important;
}
.el-carousel__arrow:hover {
  background-color: transparent !important;
}
.el-carousel__arrow.el-carousel__arrow--left {
  inset-inline-start: 1.66rem;
}
.el-carousel__arrow.el-carousel__arrow--right {
  inset-inline-end: 1.66rem;
}
.page2 {
  width: 100%;
  padding: 1rem 1.2rem;
  background-image: url(../assets/images/bg1.jpg);
  background-repeat: no-repeat;
  background-position: 50%;
  background-size: cover;
  box-sizing: border-box;
}
.page3 {
  width: 100%;
  position: relative;
  padding: 1rem 1.2rem;
  background-image: url(../assets/images/bg2.jpg);
  background-repeat: no-repeat;
  background-position: 50%;
  background-size: cover;
  box-sizing: border-box;
}

/* 定义动画效果 */
@keyframes slideInFromRight {
  0% {
    transform: translateX(100%); /* 初始位置：从右侧外部进入 */
    opacity: 0; /* 初始透明度为 0 (完全透明) */
  }
  100% {
    transform: translateX(0); /* 结束位置：正常位置 */
    opacity: 1; /* 结束透明度为 1 (完全不透明) */
  }
}

/* 应用动画的元素样式 */
.element {
  animation: slideInFromRight 1s ease-out forwards;
}

/* 定义动画效果 */
@keyframes slideInFromLeft {
  0% {
    transform: translateX(-100%); /* 初始位置：从右侧外部进入 */
    opacity: 0; /* 初始透明度为 0 (完全透明) */
  }
  100% {
    transform: translateX(0%); /* 结束位置：正常位置 */
    opacity: 1; /* 结束透明度为 1 (完全不透明) */
  }
}
.element2 {
  animation: slideInFromLeft 1s ease-out forwards;
}

@keyframes move___2nplz {
  0% {
    left: 0;
  }

  to {
    left: -66.66%;
  }
}

/* 容器设置 */
.scroll-container {
  overflow: hidden;
  position: absolute;
  top: 50px;
  left: 0;
  display: flex;
  width: 200%;
  /* height: 50px; */
  animation-duration: 36s;
  animation-timing-function: linear;
  animation-delay: 1s;
  animation-iteration-count: infinite;
  animation-direction: normal;
  animation-fill-mode: none;
  animation-play-state: running;
  animation-name: move___2nplz;
}
.scroll-container2 {
  top: 150px;
  left: 0;
  animation-duration: 26s;
}
.scroll-container3 {
  top: 250px;
  left: 0;
}
/* 鼠标悬停时暂停动画 */
.scroll-container:hover {
  animation-play-state: paused; /* 鼠标悬停时暂停动画 */
}
.scroll-container img {
  display: inline-block;
  width: 33%;
  height: 100%;
  object-fit: cover;
  border-left: 1px solid #fff;
  text-align: center;
  margin-top: 0.05rem;
  margin-right: 0.35rem;
}
</style>