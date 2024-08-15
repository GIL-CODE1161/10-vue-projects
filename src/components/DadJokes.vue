<template>
    <div class="main-cover">
        <div class="dad-jokes-container">
            <h2 class="dad-jokes-title">Dad Joke</h2>
            <div v-if="joke" class="dad-joke">{{joke}}</div>
            <button class="get-joke-button" @click="fetchJoke">Get Dad Joke</button>
        </div>
    </div>
    
</template>

<script >
import { ref } from 'vue';
import axios from 'axios'

export default  {
    name: 'DadJokes',
    setup() {
        const joke = ref(null)

            const fetchJoke = async () => {
                try {
                    const res = await axios.get('https://icanhazdadjoke.com/', {
                        headers: {Accept : 'Application/json'}

                    })
                    joke.value = res.data.joke
                } catch (error) {
                    console.error("Error fetching dad joke", error)
                    
                }
            }

            return {
                fetchJoke,
                joke
            }


        
    }

}
    

        
           
            
            
        
    
</script>

<style  scoped>

.main-cover {
    max-width: 624px;
    margin: 50px auto;
    background-image: linear-gradient(#335C81, #FFFFFF);
    border:1px solid #ccc;
    border-radius: 8px;
}
.dad-jokes-container {
    max-width: 400px;
    margin: 50px auto;
    text-align: center;
    text-decoration:bisque;

  }
  
  .dad-jokes-title {
    font-size: 24px;
    color: #333;
    margin-bottom: 20px;
    text-align: center;
    font-style: italic;

  }
  
  .get-joke-button {
    padding: 10px 15px;
    font-size: 16px;
    background-color: #4caf50;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    margin:15px auto;
    display: block;
  }
  
  .get-joke-button:hover {
    background-color: #45a049;
  }
  
  .dad-joke {
    border: 1px solid #ddd;
    border-radius: 4px;
    padding: 15px;
    margin-top: 20px;
    background-color: #f9f9f9;
    color: #333;
    font-size: 20px;
  }

</style>