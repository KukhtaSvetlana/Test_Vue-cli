<template>
    <div class="generator">
        <form class="Form">
            <p><b>Длина:</b><br>
                <input type="text" v-model="message">
            </p>
            <p><b>Цыфры: </b>
                <input type="checkbox" id="checkbox" v-model="checkedNumbers">
            </p>
            <p><b>Заглавные: </b>
                <input type="checkbox" id="checkbox" v-model="checkedUppercase">
            </p>
            <p><b>Спецсимволы: </b>
                <input type="checkbox" id="checkbox" v-model="checkedSpecialCharacters">
            </p>
            <button type="button" @click="greet(message)">Generate</button>
            <button type="button" @click="copy_to_biefer">Copy</button>
            <p>{{password}}</p>
        </form>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                message: 0,
                checkedNumbers: null,
                checkedUppercase: null,
                checkedSpecialCharacters: null,
                password: ''
            }
        },
        methods: {
            greet(message) {
                let characters = 'abcdefghijklmnopqrstuvwxyz';
                let array = "";
                array = characters;
                if (this.checkedNumbers === true) {
                    array += '1234567890';
                }
                if (this.checkedUppercase === true) {
                    array += characters.toUpperCase();
                }
                if (this.checkedSpecialCharacters === true) {
                    array += "!@#$%^&*()";
                }
                let col = array.length;
                let password = '';
                for (let i = 0; i < message; i++) {
                    password += array[Math.floor(Math.random() * col)];
                }
                this.password = password;
            },
            copy_to_biefer() {
                navigator.clipboard.writeText(this.password)
            }
        }
    }
</script>
