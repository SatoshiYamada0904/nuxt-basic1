<!-- _id folder to go to any value of host/joke/# -->
<template>
    <div>
        <nuxt-link to="/jokes">Back to Jokes</nuxt-link>
        <h2>{{joke}}</h2>
        <hr />
        <small>Joke ID: {{$route.params.id}}</small>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    data(){
        return{
            joke:null
        }
    },
    head(){
        return {
            title: this.joke,
            meta:[
                {
                    hid: "description,hid",
                    name: "description,name",
                    content: "best place for corny dad jokes"
                }
            ]
        }
    },
    async created(){
        const config = {
            headers:{
                Accept:'application/json'
            }
        }
        
        try{
            const res = await axios
            .get(`https://icanhazdadjoke.com/j/${this.$route.params.id}`, config);
            //console.log(res.data);
            this.joke = res.data.joke;

        }catch(err){
            console.log(err)
        }
    },
}
</script>

<style>

</style>