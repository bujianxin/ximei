<template>
  <div id="app">
    <a-layout id="components-layout-demo-top-side-2">
    <a-layout-header class="header">
      <div class="logo" />
    </a-layout-header>
    <a-layout>
      <a-layout-sider width="220" style="background: #fff">
        <a-menu
          mode="inline"
          :default-selected-keys="['1']"
          :default-open-keys="['sub1']"
          :style="{ height: '100%', borderRight: 0 }"
          @click="menuClick"
        > 
          <a-menu-item key="/store" >
            门店管理
          </a-menu-item>
          <a-menu-item key="/customer" >
            用户管理
          </a-menu-item>
          <a-menu-item key="/2">
            预约订单管理
          </a-menu-item>
          <a-menu-item key="3">
            服务订单管理
          </a-menu-item>
          <a-menu-item key="4">
            服务项目管理
          </a-menu-item>
          <a-menu-item key="4">
            营销管理
          </a-menu-item>
          <a-menu-item key="4">
            优惠券管理
          </a-menu-item>
          <a-menu-item key="4">
            渠道管理
          </a-menu-item>

        </a-menu>
      </a-layout-sider>
      <a-layout style="padding: 0 24px 24px">
        <a-layout-content
          :style="{ background: '#fff', padding: '24px', margin: 0, minHeight: '880px', height:'100%' }"
        >
        <router-view />
        </a-layout-content>
      </a-layout>
    </a-layout>
  </a-layout>
  </div>
</template>

<script>
export default {
  name: 'App',
  methods: {
    menuClick(item) {
      this.$router.push(item.key);
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
#components-layout-demo-top-side-2 .logo {
  width: 120px;
  height: 31px;
  background: rgba(255, 255, 255, 0.2);
  margin: 16px 28px 16px 0;
  float: left;
}
</style>
