<template xmlns:v-slot="http://www.w3.org/1999/XSL/Transform">
    <div>
        <a-drawer
                placement="right"
                :closable="false"
                @close="onClose"
                :visible="visible"
        >
            <template v-slot:handle>
                <div class="handle" @click="visible = !visible">
                    <a-icon :type="visible ? 'close' : 'setting'"></a-icon>
                </div>
            </template>
            <div>
                <h2>整体风格定制</h2>
                <a-radio-group
                        :value="$route.query.navTheme||'dark'"
                        @change="e=>handleSettingChange('navTheme',e.target.value)">
                    <a-radio value="dark">黑色</a-radio>
                    <a-radio value="light">白色</a-radio>
                </a-radio-group>
                <h2>导航模式</h2>
                <a-radio-group :value="$route.query.navLayout||'left'"
                        @change="e=>handleSettingChange('navLayout',e.target.value)">
                    <a-radio value="left">左侧</a-radio>
                    <a-radio value="top">顶部</a-radio>
                </a-radio-group>
            </div>
        </a-drawer>
    </div>
</template>
<script>
  export default {
    data() {
      return {
        visible: false,
      };
    },
    methods: {
      onClose() {
        this.visible = false;
      },
      handleSettingChange(type,value){
        this.$router.push({
          query:{...this.$route.query,[type]:value}
        })
      }
    }
  };
</script>
<style>
    .handle {
        position: absolute;
        top: 240px;
        right: 256px;
        height: 48px;
        width: 48px;
        text-align: center;
        line-height: 48px;
        font-size: 20px;
        background: #eeaafe;
        color: #fff;
        border-radius: 3px 0 0 3px;
    }
</style>
