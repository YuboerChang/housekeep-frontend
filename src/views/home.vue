<template>
  <el-container>
    <el-header>
      <div class="header-box">
        <span class="menu-collapse-box" @click="setCollapse">
          <img src="@/assets/static/menu-icon.png" class="img-box" />
          <span v-if="!isCollapse">点击折叠菜单</span>
          <span v-if="isCollapse">点击展开菜单</span>
        </span>
        <span>
          <UserMenu />
        </span></div
    ></el-header>
    <el-container>
      <el-aside :class="{ collapsed: isCollapse }">
        <Menu :isCollapse="isCollapse"></Menu>
      </el-aside>
      <el-main>
        <RouterView />
      </el-main>
    </el-container>
  </el-container>
</template>
<script>
import Menu from "@/components/menu";
import UserMenu from "@/components/user-menu";

export default {
  components: { Menu, UserMenu },
  data() {
    return {
      isCollapse: false,
      block: true,
      toggle: false,
    };
  },
  methods: {
    setCollapse() {
      this.isCollapse = !this.isCollapse;
      this.block = !this.block;
      this.toggle = !this.toggle;
    },
  },
  mounted() {
    if (true) {
      this.$router.push({
        name: "welcome",
      });
    }
  },
  setup() {},
};
</script>
<style scoped>
@import url("@/assets/css/global-cpns.css");

.el-container {
  height: 100%;
  margin: 0px;
  padding: 0px;
}
.el-header {
  width: 100%;
  height: 50px;
  padding: 0px;
}
.el-aside {
  width: 220px;
}
.el-aside.collapsed {
  width: 50px;
}
.el-main {
  padding: 30px 20px;
}
.header-box {
  display: flex;
  justify-content: space-between;
}
.menu-collapse-box {
  display: flex;
  align-items: center;
  font-size: 12px;
  width: 220px;
  cursor: pointer;
}
.img-box {
  width: 40px;
  height: 40px;
  margin: 5px 20px;
}
</style>
