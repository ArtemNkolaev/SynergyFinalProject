<template>
    <div>
        <h2 class="title">Одинокйи баскетболист</h2>
        <p class="desk">Сайт для баскетболистов, которые хотят провести время в одиночестве, пообщаться с самим собой.</p>
        <br>
        <p>____________________________________</p>
        <br>
        <p class="auth">Пройдите авторизацию:</p>
        <div v-if="isAuth">
            <div>Приветствие <b>{{ username }}</b></div>
            <button @click="logout">Выйти</button>
        </div>
        <div v-else>
            <label class="nameI" for="">Ведите имя</label>   
            <input v-model="username" @keyup.enter='login' type="text">
            <button @click="login">Вoйти</button>
        </div>


    </div>



</template>


<script>
export default {
    name: 'HomePage',


    data() {
        return{
            isAuth: false,
            username: ''
        }
    },


    methods: {
        login() {
            if (this.username !== '') {
                this.isAuth = true;
                localStorage.setItem('isAuth', true)
                localStorage.setItem('username', this.username)

                this.$router.push({
                    name: 'Chat',
                    query: {username: this.username}
                })
            } else {
                alert('ВВедите имя')
            }
            },


            logout() {
                this,this.isAuth = false;
                this.username = '';
                localStorage.removeItem('isAuth')
                localStorage.removeItem('username')
            }
            

    },

    created() {
        if (localStorage.getItem('isAuth')) {
            this.isAuth = true;
            this.username = localStorage.getItem('username')
        }
    }
}
</script>


<style scoped>

    div {
        padding:  30px;
        font-size: 22px;
    }

    label {
         margin: 0 15px;
    }

    button{ 
        background-color: rgb(247, 195, 127);
        border-radius: 8px ;
        border-style: none;
        height: 23px;
        font-family: 'Raleway', sans-serif;
        margin-left: 6px;
        transition-property: all;
        transition: all ease 200ms;
    }

    button:hover {
        transform: scale(1.2);
        transition: 200ms;
    }

    .title {
        font-family: 'Russo One', sans-serif;
        font-size: 4em;
        color: white;
        margin: 10px;
     }

    .desk {
        font-family: 'Raleway', sans-serif;
        font-size: larger;
        font-weight: bold;
    }

    .auth {
        font-family: 'Russo One', sans-serif;
        font-size: 60px;
    }

    .nameI {
        font-family: 'Raleway', sans-serif;
        font-weight: bold;
    }

    input {
        background-color: rgb(247, 195, 127);
        border-radius: 8px ;
        border-style:none;
        transition-property: all;
        transition: all ease 200ms;
        height: 20px;
    }

    input:active {
        
        transform: scale(1.3);
        transition: 200ms
    }

</style>\


<style>
    body {
        background-color: coral;
        background-repeat: no-repeat;
        background-size: cover;

        padding: 0;
        margin: 0;
    }
</style>