<template>
    <div class="app" id="app">
        <div class="l-Header">
            <h1 class="h-Logo">Instagramの画像を保存するアプリケーション</h1>
        </div>
        <div class="l-Main">
            <div class="l-Main_Primary">
                <form class="p-inputForm">
                    <input type="text"
                           name="instagram-url"
                           v-model="inputUrl"
                           placeholder="urlを入力してください"
                           autocomplete="off">
                    <button type="button"
                            name="rewrite-button"
                            v-on:click="clickHandler(inputUrl)">生成する</button>
                </form>
                <p class="p-GenerateImage">
                    <img v-bind:src="url" alt="">
                </p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            url: '',
            inputUrl: '',
        }
    },
    methods: {
        clickHandler: function(inputUrl) {
            this.url = this.inputUrl
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
