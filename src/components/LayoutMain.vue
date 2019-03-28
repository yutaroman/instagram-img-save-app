<template>
    <main class="l-Main">
        <div class="l-Main_Container">
            <div class="l-Main_Primary">
                <primary-input-form
                    v-bind:inputUrl="inputUrl"
                    v-bind:imageUrl="imageUrl"
                    v-on:generate-event="generateUrl"
                    v-on:reset-event="resetUrl"></primary-input-form>
                <primary-generate-image
                    v-bind:imageUrl="imageUrl"></primary-generate-image>
            </div>
        </div>
    </main>
</template>


<script>
    import PrimaryInputForm from './parts/PrimaryInputForm.vue';
    import PrimaryGenerateImage from './parts/PrimaryGenerateImage.vue';
    const ADD_PARAM = 'media/?size=l';
    export default {
        name: "layout-main",
        data() {
            return {
                imageUrl: '',
                inputUrl: '',
            }
        },
        components: {
            PrimaryInputForm,
            PrimaryGenerateImage,
        },
        methods: {
            generateUrl(inputedUrl) {
                let url = inputedUrl;
                if (url !== '') {
                    // パラメータが入っていれば削除
                    if (url.indexOf('?')) {
                        url = url.replace(/\?.*$/,"");
                    }
                    // 末尾にスラッシュが入ってなければ追加
                    if (url.substr(-1) !== '/') {
                        url = `${url}/`;
                    }
                    // img タグに bind する変数を変更する
                    this.imageUrl = url + ADD_PARAM;
                }
            },
            resetUrl() {
                this.imageUrl = '';
                this.inputUrl = '';
            },
        }
    }
</script>


<style lang="scss">
    .l-Main {
        margin-top: 40px;
        padding: 0 20px;
        min-height: calc(100vh - 140px);
    }
    .l-Main_Container {
        max-width: 1010px;
        margin: 0 auto;
    }
    .l-Main_Primary {
        > :first-child {
            margin-top: 0;
        }
    }
</style>
