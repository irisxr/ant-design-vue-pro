<template>
    <div :class="[`nav-theme-${navTheme}`,`nav-layout-${navLayout}`]">
        <a-layout id="components-layout-demo-side" style="min-height: 100vh">
            <a-layout-sider
                    v-if="navLayout==='left'"
                    :theme="navTheme"
                    :trigger="null"
                    collapsible
                    v-model="collapsed"
            >
                <div class="logo">Ant Design Vue Pro</div>
                <sider-meau/>
            </a-layout-sider>
            <a-layout>
                <a-layout-header style="background: #fff; padding: 0">
                    <a-icon class="trigger"
                            :type="collapsed ? 'menu-unfold':'menu-fold'"
                            @click="collapsed = !collapsed"
                    ></a-icon>
                    <Header/>
                </a-layout-header>
                <a-layout-content style="margin: 0 16px">
                    <router-view></router-view>
                </a-layout-content>
                <a-layout-footer style="text-align: center">
                    <Footer/>
                </a-layout-footer>
            </a-layout>
        </a-layout>
        <settingDrawer/>
    </div>
</template>
<script>
  import Header from "./Header.vue";
  import Footer from "./Footer.vue";
  import SiderMeau from "./SiderMeau.vue";
  import settingDrawer from "../components/settingDrawer/settingDrawer";

  export default {
    data() {
      return {
        collapsed: false
      };
    },
    computed: {
      navTheme() {
        return this.$route.query.navTheme || "dark";
      },
      navLayout() {
        return this.$route.query.navLayout || "left";
      }
    },
    components: {
      Header,
      Footer,
      SiderMeau,
      settingDrawer
    }
  };
</script>

<style scoped>
    .trigger {
        padding: 0 20px;
        line-height: 64px;
        font-size: 20px;
    }

    .trigger:hover {
        width: 60px;
        background-color: #eeeeee;
    }

    .logo {
        height: 32px;
        line-height: 32px;
        text-align: center;
        overflow: hidden;
    }

    .nav-theme-dark >>> .logo {
        color: #ffffff;
    }
</style>