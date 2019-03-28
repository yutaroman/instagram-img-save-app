<template>
    <header class="l-Header">
        <div class="l-Header_Container">
            <header-logo></header-logo>
        </div>
    </header>
</template>


<script>
    import HeaderLogo from './parts/HeaderLogo.vue';
    export default {
        name: 'layout-header',
        components: {
            HeaderLogo,
        }
    }
</script>


<style lang="scss">
    .l-Header {
        box-sizing: border-box;
        background-color: #fff;
        border-top: 1px solid rgba(0, 0, 0, .0975);
        border-bottom: 1px solid rgba(0, 0, 0, .0975);
    }
    .l-Header_Container {
        max-width: 1010px;
        min-height: 50px;
        margin: 0 auto;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
    }
</style>
