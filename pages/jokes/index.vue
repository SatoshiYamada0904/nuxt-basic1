<!-- host/jokes then it works -->
<template>
  <div>
      <SearchJokes v-on:search-text="searchText"/>
      <Joke v-for="e in jokes" :key="e.id"
        :id="e.id" :joke="e.joke"
        />

  </div>
</template>
<script>
import axios from "axios";
import Joke from "../../components/Joke"
import SearchJokes from "../../components/SearchJokes"

export default {
    components:{
        Joke
    },
    data (){
        return{
            jokes:[]
        }
    },
    async created(){
        const config = {
            headers:{
                Accept:'application/json'
            }
        }
        
        try{
            const res = await axios.get('https://icanhazdadjoke.com/search', config);
            //console.log(res.data);
            this.jokes = res.data.results;

        }catch(err){
            console.log(err)
        }
    },
    //use here for SEO
    head(){
        return {
            title: "Dad Jokes",
            meta:[
                {
                    hid: "description,hid",
                    name: "description,name",
                    content: "best place for corny dad jokes"
                }
            ]
        }
    },
    methods:{
        async searchText(text){
            const config = {
                headers:{
                    Accept:'application/json'
                }
            }
            
            try{
                const res 
                 = await axios.get(`https://icanhazdadjoke.com/search?term=${text}`,config);
                //console.log(res.data);
                this.jokes = res.data.results;

            }catch(err){
                console.log(err)
            }
        }
    }
}
</script>

<style>

</style>