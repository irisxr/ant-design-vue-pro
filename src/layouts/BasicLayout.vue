<template>
    <div>
        <Header/>
        <SiderMeau/>
        <router-view></router-view>
        <Footer/>
    </div>
</template>
<script>
    import Header from 'Header.vue'
    import Footer from 'Footer.vue'
    import SiderMeau from 'SiderMeau.vue'
    export default {
      component:{
        Header,
        Footer,
        SiderMeau
      }
    };
</script>

<style>

</style>