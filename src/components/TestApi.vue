<template>

    <img class="fPic" src="../assets/qgpJ_TVz3bA.png" alt="">
    <img class="sPic" src="../assets/qgpJ_TVz3bA.png" alt="">
    <img class="tPic" src="../assets/qgpJ_TVz3bA.png" alt="">
    <img class="uPic" src="../assets/qgpJ_TVz3bA.png" alt="">
 

    <div class="container" >
        <h1 class="title">Команды</h1>
        
 
        
        <div  class="data">
            <table >
            <tr v-for="(el, i) in teamData" :key="el.id">
                <th style="padding-right: 30px;">{{ i + 1 }} </th>
                <th >{{ el.abbreviation }}</th>
                <th> {{ el.city }}</th>
                <th><img
                        src="../assets/derlete.png"
                        alt="del"
                        @click="removeTeam(el.id)"
                        class="delBtn"
                         >
                    </th>
            </tr>

        </table>
    </div>
</div>
</template>


<script>


    export default {
        data() {
            return {
                teamData: [],
                isLoad: true
            }
        },

        mounted () {

            const url ='https://free-nba.p.rapidapi.com/teams?page=0';
            const options = {
                method: 'GET',
                headers: {
                    'X-RapidAPI-Key': '2a39c8d49cmsh3cb896c8719771cp1afbe4jsnea2bfc67574d',
                    'X-RapidAPI-Host': 'free-nba.p.rapidapi.com'
                },
            };


            fetch(url, options)
                .then((res) => res.json())
                .then((res) => {
                    this.teamData = res.data;
                    this.isload = false;
                })
        },


        methods: {
            removeTeam(id) {
                this.teamData= this.teamData.filter((el) => el.id !== id);
                
            }
        }
    }
</script>


<style scoped>
     .container {
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
     }


    .delBtn{
        width: 20px;
        height: 20px;
        border-radius: 4px;

    }

    .delBtn:hover {
        transition: 0.3s;
        scale: 1.1;
    }

     .title {
        font-family: 'Russo One', sans-serif;
        font-size: 4em;
        color: white;
        margin: 10px;
     }

     th {
        font-family: 'Raleway', sans-serif;
     }

     .data {
        font-size: 23px;
        padding: 20px ;
     }


     .delBtn{
        cursor: pointer;
        margin-left: 10px;
     }

 
     .fPic{
        position: absolute;
        width: 500px;
        right: 450px;
        top: 500px;
     }

     .sPic {
        position: absolute;
        width: 500px;
        top: 80px;
        left: 30px;
        rotate: 50deg;
     }

     .tPic{
        position: absolute;
        rotate: 90deg;
        width: 400px;
        top: 100px ;
        right: 10px;
        
     }

     .uPic {
        position: absolute;
        width: 500px;
        top: 600px;
        padding-right:700px ;
     }



</style>