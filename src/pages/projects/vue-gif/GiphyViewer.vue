<template>
    <div>
        <div class="search-box">

            <!-- takes the input and puts it into the variable of "text" and on key up
            allows you to search for it once the enter is pushed -->

            <input type="text" v-model="term" v-on:keyup.enter="searchGiphy" />
            <b-button class="" variant="primary" @click="searchGiphy">Search</b-button> 


            <b-button class="float-end" variant="primary" @click="trendingGif">Back to Trending</b-button> 

            <b-button class="float-end" variant="secondary" @click="randomGif">Find random gif</b-button> 

        </div>

        <b-card-group columns>
            <b-card
                v-for="gif in gifs"
                :key="gif.id" 
                :img-src="gif.images.fixed_width.url"
                :img-alt="gif.title" 
                img-top
            >
                <b-card-text>
                    <a :href="gif.url" target="_blank">{{ gif.title }}</a>
                </b-card-text>
            </b-card>
        </b-card-group >

        <!-- this will be how you do it in the CA to return the data from the API to the web browser
              you need to go into the vue in the console, then look for the url you need so in this case
             it is images.fixed_width.url-->

        <!-- <img :src="gifs[1].images.fixed_width.url" alt="" />
        <p>{{ gifs[1].title}}</p> -->
    </div>
</template>

<script>
import axios from 'axios'

//using constants for the API key instead of ctrl + c the link everytime

const GIPHY_URL = "https://api.giphy.com/v1/gifs";
const API_KEY = "sxPrhMgOw3mTD4QX68kFHrbLy37OA88P";

    export default{
        name: 'GiphyViewer',
        data(){
            return{
                gifs:[],
                term: ""
            };
        },

        //mounted will run before our method
        //inside mounted will be where you want to get some data, which is coming from GIPHY
        //we will do this by using AXIOS 

        
        mounted(){
            //example of how to write a chain method in javascript
            this.trendingGif()


                // EXPLINATION OF THE ARROW FUNCTION

                // => is a function. The word before it is the parameter and what comes after is what is returned
                // eg. material => material.length // (material, param1) => material.length

                // instead of:
                // function myFun(material, param1){
                //  return matrial.length
                // }              
        },

        methods:{

            randomGif(){
                
                axios.get(`${GIPHY_URL}/random?api_key=${API_KEY}`)
                .then((response) =>{
                    console.log(response.data.data)

                    //becomes an array
                    this.gifs = [response.data.data]
                })
                .catch(error => console.log(error))
            },

            searchGiphy(){

                //if this is blank
                if(!this.term){
                    alert("Please enter a search term!");

                    //this is needed to allow the method will return, meaning that the second part will not run
                    //if it has been returned
                    return;
                }


                //basically we take the axios, get the api key and gif url and slap the term at the end

                axios.get(`${GIPHY_URL}/search?api_key=${API_KEY}&q=${this.term}&limit=20`)
                .then((response) =>{
                    console.log(response.data.data)
                    this.gifs = response.data.data
                })
                .catch(error => console.log(error))
            },

            trendingGif(){

                axios.get(`${GIPHY_URL}/trending?api_key=${API_KEY}`)

                .then((response) =>{
                    console.log(response.data.data)
                    this.gifs = response.data.data
                })

                .catch(error => console.log(error))
             }

            
        }
    }
</script>

<style>

.search-box{
    margin-top: 20px;
    margin-bottom: 20px;
}

.card{
    margin-bottom: 20px;
}

@media (min-width: 34em) {
    .card-columns {
        -webkit-column-count: 2;
        -moz-column-count: 2;
        column-count: 2;
    }
}
@media (min-width: 48em) {
    .card-columns {
        -webkit-column-count: 3;
        -moz-column-count: 3;
        column-count: 3;
    }
}
@media (min-width: 62em) {
    .card-columns {
        -webkit-column-count: 4;
        -moz-column-count: 4;
        column-count: 4;
    }
}
@media (min-width: 75em) {
    .card-columns {
        -webkit-column-count: 5;
        -moz-column-count: 5;
        column-count: 5;
    }
}

</style>
