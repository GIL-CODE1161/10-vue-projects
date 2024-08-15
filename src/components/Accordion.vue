<template>
    <div class="cover">
        <h1>Accordion</h1>
        <div class="accordion-container">
            <div v-for="(item, index) in items" :key="index" class="accordion">
                <div class="accordion-header" @click="toggleAccordion(index)">
                    {{ item.title }}
                    <span class="arrow-icon" >{{item.open ? "▼" : "▶"}}</span>
                </div>
                <div v-show="item.open" class="accordion-content">{{item.content}}</div>
            </div>
        </div>

    </div>
</template>

<script>
import { ref } from 'vue'
    export default {
        // eslint-disable-next-line vue/multi-word-component-names
        name: 'Accordion',
        setup() {
            const items = ref([
                {
                title: 'What is HTML',
                content: 'Hypertext Markup Language is the standard markup language for documents designed to be displayed in a web browser. It defines the content and structure of web content. It is often assisted by technologies such as Cascading Style Sheets and scripting languages such as JavaScript.',
                open: false
                },
                {
                title: 'What is CSS',
                content: 'CSS stands for Cascading Style Sheets, and is a computer language used to structure and style web pages written in HTML or XML. CSS files, also called cascading style sheets, contain coding elements that specify how HTML elements should appear on screen, paper, or other media',
                open: false
                },
                {
                title: 'What is JS',
                content: 'JavaScript, often abbreviated as JS, is a programming language and core technology of the Web, alongside HTML and CSS. 99% of websites use JavaScript on the client side for webpage behavior. Web browsers have a dedicated JavaScript engine that executes the client code',
                open: false
                },
                {
                title: 'What is REACT',
                content: 'React is a free and open-source front-end JavaScript library for building user interfaces based on components by Facebook Inc. It is maintained by Meta and a community of individual developers and companies',
                open: false
                },
                {
                title: 'What is VUE',
                content: 'Vue.js is an open-source model–view–viewmodel front end JavaScript framework for building user interfaces and single-page applications. It was created by Evan You and is maintained by him and the rest of the active core team members',
                open: false
                }
                


            ])
            const toggleAccordion = (index) => {
                items.value = items.value.map((item, i) => ({
                    ...item,
                    open: i === index ? !item.open : false

                }))
            }
            return {
                items,
                toggleAccordion,
                
            }
        }
    }
</script>

<style  scoped>
.cover {
    max-width: 650px;
    border: 1px solid #ddd;
    margin: 50px auto;
    background-image: linear-gradient(#EFE9F4, #5078F2);
    border-radius: 8px;
}

h1 {
    color: #292727;
    text-align: center;
    font-style: italic;
}
.accordion-container {
    max-width: 600px;
    margin: 50px auto;
  }
  
  .accordion {
    border: 1px solid #ddd;
    border-radius: 4px;
    overflow: hidden;
    margin-bottom: 10px;
  }
  
  .accordion-header {
    background-color: #3498db;
    color: #fff;
    padding: 15px;
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .arrow-icon {
    font-size: 20px;
  }
  
  .accordion-content {
    padding: 15px;
    display: none;
    border-top: 1px solid #ddd;
    background-color: #f9f9f9;
    color: #333;
  }
  
  .accordion-content[style] {
    display: block;
  }

</style>