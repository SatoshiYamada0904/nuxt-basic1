<!-- no need to set up reouter or anything. 
just make about.vue then host/about will show this page-->
<template>
  <div>
    <h1>Abount DadJokes</h1>
    <p>This is an app that shows corny dad jokes</p>
  </div>
</template>

<script>
export default {
    //use here for SEO
    head(){
        return {
            title: "About Us",
            meta:[
                {
                    hid: "description,hid",
                    name: "description,name",
                    content: "best place for corny dad jokes"
                }

            ]
        }

    }
}
</script>

<style>

</style>
