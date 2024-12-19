<template>
  <div id="app">
    <el-container>
      <el-header :style="navStyle">
        <Header></Header>
      </el-header>
      <el-main style="padding: 0"> <Home></Home> </el-main>
    </el-container>
  </div>
</template>

<script>
import Header from "./components/Header_.vue";
import Home from "./views/home.vue";

export default {
  name: "App",
  components: {
    Header,
    Home,
  },
  data() {
    return {
      navBgColor: "",
      lastScrollY: 0, // 记录上一次的滚动位置
      navVisible: true, // 是否显示导航栏
    };
  },
  computed: {
    navStyle() {
      return {
        backgroundColor:
          this.navBgColor === "rgba(0,0,0,.8) !important"
            ? "rgba(0,0,0,.8) !important"
            : "", // 动态背景颜色
        transform: this.navVisible
          ? "translate(0)"
          : "translateY(-100%)",
        transition: "transform 0.3s ease", // 平滑过渡
      };
    },
  },
  mounted() {
    const html = document.documentElement;
    const width = html.clientWidth || window.innerWidth;

    // 根据屏幕宽度来设置根字体大小，这里以 375px 作为基准
    html.style.fontSize = width / 14.4 + "px";
    // 监听页面尺寸变化
    window.addEventListener("resize", this.handleResize);
    window.addEventListener("scroll", this.handleScroll);
  },
  beforeDestroy() {
    // 组件销毁前移除事件监听
    window.removeEventListener("resize", this.handleResize);
    window.removeEventListener("scroll", this.handleScroll);
  },
  methods: {
    handleResize() {
      const html = document.documentElement;
      const width = html.clientWidth || window.innerWidth;

      // 根据屏幕宽度来设置根字体大小，这里以 375px 作为基准
      html.style.fontSize = width / 14.4 + "px";
    },

    handleScroll() {
      const currentScrollY = window.scrollY;

      if (currentScrollY > 0) {
        this.navBgColor = "rgba(0,0,0,.8) !important"; // 滚动时的背景颜色（深色）
      } else {
        this.navBgColor =
          "linear-gradient(rgba(0,0,0,.6),transparent) !important"; // 滚动到顶部时的背景颜色（透明）
      }
      console.log(this.navBgColor);

      // 如果当前滚动位置大于上一次的位置，则是向下滚动
      if (currentScrollY > this.lastScrollY) {
        this.navVisible = false; // 隐藏导航栏
      } else {
        this.navVisible = true; // 显示导航栏
      }

      // 更新上次滚动位置
      this.lastScrollY = currentScrollY;
    },
  },
};
</script>

<style>
body {
  margin: 0;
  font-size: 16px;
}
.el-header {
  position: fixed;
  top: 0;
  background: linear-gradient(rgba(0, 0, 0, 0.6), transparent) !important;
  width: 100%;
  height: 0.8rem !important;
  line-height: 0.8rem;
  z-index: 9999;
  border-left: none;
  border-right: none;
  box-sizing: border-box;
  padding: 0 !important;
}
</style>
