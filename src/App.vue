<template>
    <div class="app" id="app">
        <div class="l-Header">
            <h1 class="h-Logo">Instagramの画像を保存するアプリケーション</h1>
        </div>
        <div class="l-Main">
            <div class="l-Main_Primary">
                <form class="p-inputForm">
                    <input
                        type="text"
                        name="instagram-url"
                        v-model="inputUrl"
                        placeholder="urlを入力してください"
                        autocomplete="off">
                    <button
                        type="button"
                        name="rewrite-button"
                        v-on:click="clickHandler(inputUrl)">生成する</button>
                </form>
                <div class="p-GenerateImage">
                    <img
                        v-bind:src="imageUrl"
                        alt="">
                </div>
            </div>
        </div>
    </div>
</template>

<script>
const ADD_PARAM = 'media/?size=l';
export default {
    data() {
        return {
            imageUrl: '',
            inputUrl: '',
        }
    },
    methods: {
        clickHandler(inputUrl) {
            let url = this.inputUrl;

            // パラメータが入っていれば削除
            if (url.indexOf('?')) {
                url = url.replace(/\?.*$/,"");
            }

            // 末尾にスラッシュが入ってなければ追加
            if (url.substr(-1) !== '/') {
                url = `${url}/`;
            }

            // imgタグに bind する変数を変更する
            this.imageUrl = url + ADD_PARAM;
        }
    }
}
</script>

<style lang="scss">
@import "../node_modules/bulma/bulma.sass";
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}
</style>
