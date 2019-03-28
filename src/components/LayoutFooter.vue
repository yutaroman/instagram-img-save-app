<template>
    <footer class="l-Footer">
        <div class="l-Footer_Container">
            <footer-copyright></footer-copyright>
        </div>
    </footer>
</template>


<script>
    import FooterCopyright from './parts/FooterCopyright.vue';
    export default {
        name: 'layout-footer',
        components: {
            FooterCopyright,
        }
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
