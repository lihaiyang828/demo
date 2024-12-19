<template>
  <div class="headerBox">
    <div class="leftBox">
      <div class="logBox">
        <img src="../assets/images/logo.svg" alt="" />
      </div>
      <div class="navBox">
        <el-menu class="el-menu-demo" mode="horizontal">
          <el-submenu index="1">
            <template slot="title">模型</template>
            <el-menu-item index="1-1">选项1</el-menu-item>
            <el-menu-item index="1-2">选项2</el-menu-item>
            <el-menu-item index="1-3">选项3</el-menu-item>
          </el-submenu>
          <el-submenu index="2">
            <template slot="title">AIGC产品</template>
            <el-menu-item index="2-1">选项1</el-menu-item>
            <el-menu-item index="2-2">选项2</el-menu-item>
            <el-menu-item index="2-3">选项3</el-menu-item>
          </el-submenu>
          <el-submenu index="3">
            <template slot="title">服务</template>
            <el-menu-item index="3-1">选项1</el-menu-item>
            <el-menu-item index="3-2">选项2</el-menu-item>
            <el-menu-item index="3-3">选项3</el-menu-item>
          </el-submenu>
          <el-submenu index="4">
            <template slot="title">新闻和咨询</template>
            <el-menu-item index="4-1">选项1</el-menu-item>
            <el-menu-item index="4-2">选项2</el-menu-item>
            <el-menu-item index="4-3">选项3</el-menu-item>
          </el-submenu>
          <el-submenu index="5">
            <template slot="title">关于我们</template>
            <el-menu-item index="5-1">选项1</el-menu-item>
            <el-menu-item index="5-2">选项2</el-menu-item>
            <el-menu-item index="5-3">选项3</el-menu-item>
          </el-submenu>
        </el-menu>
      </div>
    </div>
    <div class="rightBox">
      <div>
        <el-menu class="el-menu-demo" mode="horizontal">
          <el-submenu index="1">
            <template slot="title">
              <img
                src="../assets/images/language_ic.png"
                alt=""
                style="width: 0.16rem; height: 0.16rem"
              />
              中文</template
            >
            <el-menu-item index="1-1">简体中文</el-menu-item>
            <el-menu-item index="1-2">English</el-menu-item>
          </el-submenu>
        </el-menu>
      </div>
      <div>
        <button class="header_btn">合作咨询</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Header_",
  props: {},
  data() {
    return {};
  },
  computed: {},
  mounted() {},
  beforeDestroy() {},
  methods: {},
};
</script>

<style>
.headerBox {
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin: 0 auto;
  width: 100%;
  padding-left: 1.2rem;
  padding-right: 1.2rem;
  box-sizing: border-box;
  z-index: 11;
}
.leftBox {
  display: flex;
  align-items: center;
}
.rightBox {
  display: flex;
  align-items: center;
  position: relative;
}
.logBox {
  height: 0.32rem;
  margin-right: 0.4rem;
}
.logBox img {
  display: block;
  height: 100%;
  cursor: pointer;
}
.navBox {
  display: flex;
}
.navBox .el-menu {
  background-color: transparent !important;
  color: #fff !important;
}
.navBox .el-menu.el-menu--horizontal {
  border: none;
}
.navBox .el-menu--horizontal > .el-submenu .el-submenu__title {
  border: none;
  font-size: 0.16rem;
  font-weight: 400;
  line-height: 0.36rem;
  padding-right: 0.16rem;
  padding-left: 0.16rem;
  height: 0.36rem;
  color: #fff;
  margin-right: 0.3rem;
  cursor: pointer;
}
.rightBox .el-menu {
  background-color: transparent !important;
  color: #fff !important;
}
.rightBox .el-menu.el-menu--horizontal {
  border: none;
}
.rightBox .el-menu--horizontal > .el-submenu .el-submenu__title {
  border: none;
  font-size: 0.16rem;
  font-weight: 400;
  line-height: 0.36rem;
  padding-right: 0.16rem;
  padding-left: 0.16rem;
  height: 0.36rem;
  color: #fff;
  margin-right: 0.3rem;
  cursor: pointer;
}
.rightBox .el-submenu__title i,
.navBox .el-submenu__title i {
  color: #fff;
}
.rightBox .el-menu--horizontal > .el-submenu .el-submenu__title:hover,
.navBox .el-menu--horizontal > .el-submenu .el-submenu__title:hover {
  background-color: transparent !important;
  color: #fff;
}
.header_btn {
  display: flex;
  align-items: center;
  border: 1px solid #fff;
  height: 0.32rem;
  padding-left: 0.16rem;
  padding-right: 0.16rem;
  box-sizing: border-box;
  line-height: 0.32rem;
  text-align: center;
  color: #fff;
  cursor: pointer;
  font-weight: 400;
  font-size: 0.14rem;
  white-space: nowrap;
  background-color: transparent;
}
.header_btn:hover {
  color: #fff;
  border: 2px solid #fff;
  padding-left: 0.15rem;
  padding-right: 0.15rem;
}
</style>