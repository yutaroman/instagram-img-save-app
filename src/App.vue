<template>
    <div class="app" id="app">
        <layout-header></layout-header>
        <layout-main></layout-main>
        <layout-footer></layout-footer>
    </div>
</template>


<script>
    import LayoutHeader from './components/LayoutHeader.vue';
    import LayoutMain from './components/LayoutMain.vue';
    import LayoutFooter from './components/LayoutFooter.vue';
    export default {
        components: {
            LayoutHeader,
            LayoutMain,
            LayoutFooter,
        }
    }
</script>


<style lang="scss">
    @import "./assets/styles/reset.scss";
    @import "./assets/styles/base.scss";
</style>
