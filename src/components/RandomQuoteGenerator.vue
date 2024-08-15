<template>
  <div class="quote-generator">
    <h1 class="app-title">Random Quote Generator</h1>
    <blockquote class="quote-container">
        <p>{{currentQuote.text}}</p>
        <cite>
            {{ currentQuote.author }}
        </cite>

    </blockquote>
    <button @click="getRandomQuotes" class="quote-button">Get Random Quote</button>

  </div>
</template>

<script>
import { ref , onMounted} from 'vue'
export default {
  name: 'RandomQuoteGenerator',
  setup() {
    const quotes = ref([
      {
        text: 'The only way to do great work is to love what you do',
        author: 'Steve Jobs'
      },
      {
        text: 'Believe you can and you are half-way there',
        author: 'Theodore Rooselvet'
      },
      {
        text: "Life is what happens when you're busy making other plans",
        author: 'John Lennon'
      },
      {
        text:'Before you start some work, always ask yourself three questions - Why am I doing it, What the results might be and Will I be successful. Only when you think deeply and find satisfactory answers to these questions, go ahead',
        author: 'Chanakya'
      },
      {
        text: 'I do not know anyone who has got to the top without hard work. That is the recipe.It will not always get you to the top, but should get you pretty near',
        author: 'Margareth Thatcher'
      },
      {
        text: 'Try not to become a man of success. Rather become a man of value',
        author: 'Albert Eintein'
      },
      {
        text: 'Success is stumbling from failure to failure with no loss of enthusiasm',
        author: 'Winston Churchil'
      },
      {
        text: 'It is hard to fail, but it is worse never to have tried to succeed',
        author: 'Theodore Roosevelt'
      },
      {
        text: 'Our greatest weakness lies in giving up. The most certain way to succeed is always to try just one more time',
        author: 'Thomas Edison'
      }
    ])
    const currentQuote = ref({ text: ' ', author: ' ' })

    const getRandomQuotes = () => {
        const randomIndex = Math.floor(Math.random() *quotes.value.length)
        currentQuote.value = quotes.value[randomIndex]

    }
    
    onMounted(() => {
        return getRandomQuotes

       

    })
    
    

    return {
        quotes,
        currentQuote,
        getRandomQuotes,

    }
    
    

  }
}
</script>

<style scoped>
.quote-generator {
    max-width: 600px;
    background-image: linear-gradient(#335C81, #FFFFFF) ;
    margin: 50px auto;
    padding: 20px;
    text-align: center;
    border: 1px solid #ccc;
    border-radius: 8px;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  }
  
  .app-title {
    font-size: 24px;
    font-style: italic;
    margin-bottom: 20px;
    color: #333;
  }
  
  .quote-container {
    background-color: #333;
    color: #ddd;
    font-style: italic;
    text-decoration: #ddd;
    padding: 20px;
    border-radius: 8px;
    border: 1px solid #ddd;
    margin-bottom: 20px;
  }
  
  p {
    font-size: 18px;
    margin-bottom: 10px;
  }
  
  cite {
    font-style: normal;
    color: #ddd;
  }
  
  .quote-button {
    padding: 10px 20px;
    font-size: 16px;
    background-color: #3498db;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .quote-button:hover {
 background-color: #2980b9;
  }



</style>
