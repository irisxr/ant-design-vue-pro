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
                    <a-icon :type="visible?'close':'setting'"></a-icon>
                </div>
            </template>
            <p>Some contents...</p>
            <p>Some contents...</p>
            <p>Some contents...</p>
        </a-drawer>
    </div>
</template>
<script>
  export default {
    data() {
      return {
        visible: false
      };
    },
    methods: {
      onClose() {
        this.visible = false;
      }
    }
  };
</script>
<style>
    .handle{
        position: absolute;
        top:240px;
        right: 256px;
        height: 48px;
        width: 48px;
        text-align: center;
        line-height:48px;
        font-size: 20px;
        background: #eeaafe;
        color: #fff;
        border-radius: 3px 0 0 3px;
    }
</style>