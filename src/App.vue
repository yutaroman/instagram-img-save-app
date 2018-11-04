<template>
    <div class="app" id="app">
        <header class="l-Header">
            <div class="l-Header_Container">
                <h1 class="h-Logo">Instagramで投稿された画像を保存するアプリケーション</h1>
            </div>
        </header>
        <main class="l-Main">
            <div class="l-Main_Container">
                <div class="l-Main_Primary">
                    <div class="p-inputForm">
                        <input
                            type="text"
                            name="instagram-url"
                            v-model="inputUrl"
                            placeholder="検索"
                            autocomplete="off">
                        <button
                            type="button"
                            name="rewrite-button"
                            v-on:click="setGenerateUrl(inputUrl)">生成</button>
                    </div>
                    <p class="p-GenerateImage">
                        <img
                            v-bind:src="imageUrl"
                            alt="">
                    </p>
                </div>
            </div>
        </main>
        <footer class="l-Footer">
            <div class="l-Footer_Container">
                <p class="f-Copyright">
                    <small>© 2018 yutaroman</small>
                </p>
            </div>
        </footer>
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
            setGenerateUrl(inputUrl) {
                let url = this.inputUrl;

                if (url !== '') {
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
    }
</script>

<style lang="scss">
    @import "./assets/reset.css";
    html {
        font-size: 62.5%;
        height: 100%;
    }
    body {
        font-family: "游ゴシック体", "Yu Gothic", "YuGothic", "ヒラギノ角ゴ ProN W3", "Hiragino Kaku Gothic ProN", "メイリオ", "Meiryo", sans-serif;
        font-size: 1.4rem;
        color: #333;
        line-height: 1.65;
        min-width: 100%;
        height: 100%;
    }
    img {
        height: auto;
        max-width: 100%;
    }
    #app {
        min-height: 100%;
        margin-bottom: -50px;
    }

    .l-Header {
        box-sizing: border-box;
        background-color: #fff;
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
    .h-Logo {}

    .l-Main {
        margin-top: 40px;
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
    .p-inputForm {
        display: flex;
        align-items: center;
        flex-direction: column;
        margin-top: 30px;
        input,
        button {
            margin: 0;
            padding: 0;
            background: none;
            border: none;
            border-radius: 0;
            appearance: none;
        }
        [name="instagram-url"] {
            background-image: url("./assets/icon-search.png");
            background-repeat: no-repeat;
            background-size: 10px;
            background-position: left 10px center;
            box-sizing: border-box;
            border: 1px solid #dbdbdb;
            border-radius: 3px;
            text-align: center;
            width: 75%;
            height: 30px;
            padding: 0 30px;
        }
        [name="rewrite-button"] {
            box-sizing: border-box;
            border-radius: 3px;
            border: 1px solid #dbdbdb;
            text-align: center;
            color: #262626;
            font-size: 1.6rem;
            font-weight: bold;
            width: 15%;
            height: 30px;
            margin-top: 15px;
            cursor: pointer;
        }
    }
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
    .f-Copyright {}
</style>
