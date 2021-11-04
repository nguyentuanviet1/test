<template>
<div>
    <header class="bg-gray-300 py-6">
        <div class="flex">
            <a class="flex-initial mx-5" href="">
                <h1>Pluvego</h1>
            </a>
            <div class="absolute flex-initial">Martin.D.Se <button @click=logout> déconnecter</button></div>
        </div>
    </header>
    <div>
        <!-- <b-row>
        <b-col sm="2" class="content" v-if="!isLogin">
          <b-list-group class="w-100">
            <b-list-group-item button @click.prevent="clickRouter('alertes')">Mes alertes</b-list-group-item>
            <b-list-group-item button @click.prevent="clickRouter('assets')">Mes assets</b-list-group-item>
            <b-list-group-item button @click.prevent="clickRouter('contacts')">Mes contacts</b-list-group-item>
            <b-list-group-item button @click.prevent="clickRouter('user')">Profil</b-list-group-item>
          </b-list-group>
        </b-col>
        <b-col sm="10">
        </b-col>
      </b-row> -->
        <div class="flex ">
            <div class="flex-initial w-1/6 bg-blue-200 h-screen" v-if="!isLogin">
            <div class="hover:bg-red-700" :class="{'bg-red-500': isRouteName == 'alertes'}"  @click.prevent="clickRouter('alertes')">Mes alertes</div>
            <div class="hover:bg-red-700" :class="{'bg-red-500': isRouteName == 'assets'}"  @click.prevent="clickRouter('assets')">Mes assets</div>
            <div class="hover:bg-red-700" :class="{'bg-red-500': isRouteName == 'contacts'}"  @click.prevent="clickRouter('contacts')">Mes contacts</div>
            <div class="hover:bg-red-700" :class="{'bg-red-500': isRouteName == 'user'}"  @click.prevent="clickRouter('user')">Profil</div>
            </div>
            <div class="flex-initial m-8" :class="{'w-full': isLogin, 'w-5/6': !isLogin}">

                <router-view></router-view>
            </div>
        </div>
    </div>
</div>
</template>

<script>
import {
    mapActions
} from 'vuex';
// import './index.css'
// import 'tailwindcss/tailwind.css'
// import Vue from 'vue'
// import router from '../routes';
// import VueRouter from 'vue-router';

// Vue.use(VueRouter);

// const router = new VueRouter({
//   routes: Routes,
// });
export default {
    name: "login",
    data() {
        return {
            isLogin: false,
            isRouteName: 'user'
        };
    },
    created() {
        this.int()
    },
    beforeUpdate() {
        this.int()
    },
    methods: {
        int() {
            // console.log(this.$route.name)
            if (this.$route.name === 'login') {
                this.isLogin = true
            } else {
                this.isLogin = false
            }

        },
        clickRouter(routeName = '') {
          this.isRouteName = routeName
            this.$router.push({
                name: routeName
            })
            this.int()
        },
        ...mapActions([
            'logout'
        ])
    }
}
</script>

<style>
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
}

.a {
    text-align: center;
}

.content {
    top: +75px;
    position: fixed;
    z-index: 100;
    height: 900px;
    padding: 0px;
    border-right: 1px solid black;
}

.position-fixed {
    width: 100%;
    position: fixed;
    z-index: 150;
}

.router-view {
    padding-top: 80px;
}

.note-content {
    margin: 20px;
}

.name {
    width: 180px;
    margin-top: 30px;
}

.box {
    display: flex;
    flex-wrap: nowrap;
}

.dropdown-data {
    margin-top: 20px;
    width: 120px;
}

.phone-number {
    margin-top: 20px;
}

.style-input {
    width: 400px;
}

.absolute {
    position: absolute;
    right: 0;
    /* color:; */
}

.btn-login {
    margin: 30px 180px;
}

.w-100 {
    width: 100%;
}
</style>
