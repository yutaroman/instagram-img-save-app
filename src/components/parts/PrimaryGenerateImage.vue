<template>
    <p class="p-GenerateImage">
        <img
            v-if="imageUrl === ''"
            src="../../assets/images/dummy.png"
            alt="ダミー画像">
        <img
            v-else
            v-bind:src="imageUrl"
            alt="">
    </p>
</template>


<script>
    export default {
        name: 'primary-generate-image',
        props: {
            imageUrl: String,
        }
    }
</script>


<style lang="scss">
    .p-GenerateImage {
        display: flex;
        align-items: center;
        justify-content: center;
        margin-top: 30px;
        img {
            border: solid 1px #dbdbdb;
            max-height: 500px;
        }
    }
</style>
