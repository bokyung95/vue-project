<template>
    <div class="container">
        <router-link to="/">홈</router-link>
        <router-link to="/login" @click.prevent="sayHello">{{login}}</router-link>
        <router-link to="/register">회원가입</router-link>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                login : "로그인",
                register : "회원가입"
            }
        },
        methods: {
            sayHello(){
                console.log('hello');
            }
        }
    }
</script>

<style scoped>
.container {
    width: 100%;
    display : flex;
    justify-content: space-around;
    padding: 20px;
    background: lightgray;
}
</style>
