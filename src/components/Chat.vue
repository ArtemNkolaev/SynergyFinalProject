<template>
    <h1 class="title">Поговори сам с собой </h1>
    <div v-if="user">
        <div class="chat">

            <div class="text" v-for="msg in messages" :key="msg.id">
                {{ msg.user }}: {{ msg.text }}
            </div>

            <div v-show="emptyMsg" class="empty">Сообщений нет</div>
        </div>  



        <input v-model="newMsg"  @keyup.enter='sendMsg' placeholder="Введите сообщенитк" type="text">

        <button class="but"  @click="sendMsg">Отправить</button>
        <button v-show="deleteBtn" @click="delMsg">Удалить</button>
    </div>


    <div v-else class="alert">
        Для авторизации перейдите по <router-link :to="{ name: 'Home'}">Ссылке</router-link>
    </div>
</template>


<script>
export default {
    name: 'ChatPage',

    data() {
        return {
            messages: [],
            newMsg: '',
            emptyMsg: true,
            deleteBtn: false,
            user: localStorage.getItem('username')
        }
    },

    computed() {
        localStorage.setItem('username', this.$route.query.username)
    },


    methods: {
        sendMsg() {
            if (!this.user) {
                this.user = 'Аноним'
            }


            if (this.newMsg !== '') {
                this.emptyMsg = false;
                
                this.messages.push({ id: new Date().getTime(), text: this.newMsg, user: this.user})
                
                this.deleteBtn = true;
                this.newMsg = ''
            }

            else{ 
                alert('ВВедите сообщение')
            }
        },

        delMsg() {
            this.messages =[]
            this.emptyMsg = true;
        }
    }
}
</script>


<style scoped>
    h2 {
        color: orange;
    }

    .text {
        margin-bottom:  20px;
    }

    .chat {
         width:  500px;
         /* height: 670px; */
         border-radius: 18px ;
         border: solid 3px orange;
         background-color: rgb(247, 195, 127);
         color: black;
         font-size: 18;
         font-weight: bold;
         margin: 12px;
         padding: 15px;
    }

    .empty {
        font-family: 'Raleway', sans-serif;
        font-size: x-large;
        color: white;
        display: flex;
        width: 100%;
       
        text-align: center;
        justify-content: center;
        align-items: center;
    }

    input {
        border: solid 3px orange;
        width: 300px;
        height: 100px;
        /* margin-right:10px ; */
    }


    button{
        background-color: rgb(247, 195, 127);
        border-radius: 8px;
        border-style: none;
        height: 23px;
        font-family: 'Raleway', sans-serif;
        margin-left: 6px;
        margin-left: 5px;
        /* margin-bottom: 25px; */
    }

    .alert{ 
        padding: 20px;
    }


    .title {
        font-family: 'Russo One', sans-serif;
        font-size: 4em;
        color: white;
        margin: 20px;
     };
    

    button{ 
        /* width: 7800px; */
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

</style>