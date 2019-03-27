<template>
    <div class="app" id="app">
        <layout-header></layout-header>
        <main class="l-Main">
            <div class="l-Main_Container">
                <div class="l-Main_Primary">
                    <div class="p-inputForm">
                        <input
                            type="text"
                            name="instagram-url"
                            v-model="inputUrl"
                            placeholder="コピーしたリンクを貼り付け"
                            autocomplete="off">
                        <div class="p-inputForm-button">
                            <button
                                type="button"
                                name="rewrite-button"
                                v-on:click="setGenerateUrl(inputUrl)">生成</button>
                            <button
                                type="button"
                                name="reset-button"
                                v-on:click="setResetUrl()">リセット</button>
                        </div>
                    </div>
                    <p class="p-GenerateImage">
                        <img
                            v-if="imageUrl === ''"
                            src="./assets/images/dummy.png"
                            alt="ダミー画像">
                        <img
                            v-else
                            v-bind:src="imageUrl"
                            alt="">
                    </p>
                </div>
            </div>
        </main>
        <layout-footer></layout-footer>
    </div>
</template>


<script>
    import Vue from 'vue';
    import LayoutHeader from './components/LayoutHeader.vue';
    import LayoutFooter from './components/LayoutFooter.vue';
    Vue.component('layout-header', LayoutHeader);
    Vue.component('layout-footer', LayoutFooter);

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
            },
            setResetUrl() {
                this.imageUrl = '';
                this.inputUrl = '';
            }
        }
    }
</script>


<style lang="scss">
    @import "./assets/styles/reset.scss";
    @import "./assets/styles/base.scss";
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
            background-image: url("./assets/images/icon-search.png");
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
            font-size: 1.3rem;
            font-weight: bold;
            width: 20%;
            height: 30px;
            cursor: pointer;
        }
        [name="reset-button"] {
            box-sizing: border-box;
            border-radius: 3px;
            border: 1px solid #dbdbdb;
            text-align: center;
            color: #262626;
            font-size: 1.3rem;
            font-weight: bold;
            width: 20%;
            height: 30px;
            margin-left: 15px;
            cursor: pointer;
        }
    }
    .p-inputForm-button {
        display: flex;
        justify-content: center;
        width: 100%;
        margin-top: 15px;
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
</style>
