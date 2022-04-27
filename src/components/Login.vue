<template>
    <div>
        <div>
            <input type="text" v-model="userId">
        </div>
        <div>
            <input type="password" v-model="userPw">
        </div>
        <div>
            <button @click="checkLogin">로그인</button>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            userId : '',
            userPw : '',
            id : '박보경',
            password : '12345'
        }
    },
    methods: {
        checkLogin(e) {
            // console.log(this.userId);
            if(this.userId === '' || this.userPw === ''){
                alert('아이디 또는 비밀번호를 입력해주시기 바랍니다.');
            }else{
                if(this.id === this.userId && this.password === this.userPw) {
                    alert('맞습니다.');
                }else {
                    alert('아이디와 비밀번호가 다릅니다.');
                }
            }
        }
    }
}
</script>