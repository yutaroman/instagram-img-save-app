<template>
    <footer class="l-Footer">
        <div class="l-Footer_Container">
            <footer-copyright></footer-copyright>
        </div>
    </footer>
</template>


<script>
    import Vue from 'vue';
    import FooterCopyright from './parts/FooterCopyright.vue';
    Vue.component('footer-copyright', FooterCopyright);

    export default {
        name: 'layout-footer',
    }
</script>


<style lang="scss">
    .l-Footer {
        height: 50px;
        display: flex;
        align-items: center;
        justify-content: center;
    }
    .l-Footer_Container {
        max-width: 1010px;
        margin: 0 auto;
    }
</style>
