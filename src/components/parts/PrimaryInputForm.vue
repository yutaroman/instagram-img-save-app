<template>
    <div class="p-inputForm">
        <input
            type="text"
            name="instagram-url"
            v-model="url"
            placeholder="コピーしたリンクを貼り付け"
            autocomplete="off">
        <div class="p-inputForm-button">
            <button
                type="button"
                name="rewrite-button"
                v-on:click="generateHandler()">生成</button>
            <button
                type="button"
                name="reset-button"
                v-on:click="ResetHandler()">リセット</button>
        </div>
    </div>
</template>


<script>
    export default {
        name: 'primary-input-form',
        props: {
            inputUrl: String,
            imageUrl: String,
        },
        data() {
            return {
                url: '',
            }
        },
        methods: {
            generateHandler() {
                this.$emit('generate-event', this.url);
            },
            ResetHandler() {
                this.$emit('reset-event');
            },
        }
    }
</script>


<style lang="scss">
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
            background-image: url("../../assets/images/icon-search.png");
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
</style>
