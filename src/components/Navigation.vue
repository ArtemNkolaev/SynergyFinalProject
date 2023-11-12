<template>
    <div class="container">
        <nav>
            
                <router-link class="navMenu"  to="/">Домашняя страница</router-link>
                <router-link class="navMenu" to="/chat">Чат</router-link>
                <router-link class="navMenu" to="/test">Подгрузка данных с API </router-link>

        </nav>
    </div>
</template>


<script>
export default {
    name: 'NavComp',
}
</script>


<style scoped>
    .container {
        
        border-radius: 0px  0px 30px 30px;
        font-size: 30px ;
        width: 100%;
        font-family: 'Russo One', sans-serif;
        /* backdrop-filter: blur(12px); */
        background-color: rgb(247, 195, 127);
        height: 70px;
        display: flex;
        justify-content: center;
    }

    nav {
        
        width: 1000px;
        height: 100%;
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 10px;
        
    }

    .navMenu {
        
        text-decoration: none;
        color: white;
        transition-property: all;
        transition: all ease 200ms;
    }

    .navMenu:hover{
        transform: scale(1.3);
        transition: 200ms;
    }


    



</style>