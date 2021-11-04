<template>
<div>
    <div class="flex mb-6">
        <div class="w-32"><b>Name</b></div>
        <input type="text" v-model="fromLogin.name" placeholder="Enter your name">
    </div>
    <div class="flex">
        <div class="w-32"><b>password</b></div>
        <input type="text" v-model="fromLogin.pass" placeholder="Enter your password">
    </div>
    <input type="button" class="p-2" @click.prevent="clickLogin()" value="Login">
</div>
</template>

<script>
// import Vue from 'vue'
// import router from '../routes';
// import VueRouter from 'vue-router';

// Vue.use(VueRouter);

// const router = new VueRouter({
//   routes: Routes,
// });
import {
    mapState,
    mapActions
} from 'vuex';
export default {
    name: "login",
    data() {
        return {
            fromLogin: {
                name: '',
                pass: '',
            }
        };
    },
    computed: {
        ...mapState([
            'loggingIn',
            'loginError'
        ])
    },
    mounted() {
        // console.log('sdv')
    },
    methods: {
        ...mapActions([
            'doLogin'
        ]),
        clickLogin() {
            this.doLogin({
                email: this.fromLogin.name,
                password: this.fromLogin.pass
            });
            // console.log('sdv')
        }
    }
}
</script>

<style scoped>
</style>
