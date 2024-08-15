<template>
    <div>
        <div class="main-calc">
            <h1>Calculator</h1>
            <div class="calculator">
                <input v-model="display" :class="displayClass" readonly>
    
                <div class="buttons">
                    <button @click="appendToDisplay('7')">7</button>
                    <button @click="appendToDisplay('8')">8</button>
                    <button @click="appendToDisplay('9')">9</button>
                    <button @click="appendToDisplay('/')">/</button>
    
                    <button @click="appendToDisplay('4')">4</button>
                    <button @click="appendToDisplay('5')">5</button>
                    <button @click="appendToDisplay('6')">6</button>
                    <button @click="appendToDisplay('*')">*</button>
    
                    <button @click="appendToDisplay('1')">1</button>
                    <button @click="appendToDisplay('2')">2</button>
                    <button @click="appendToDisplay('3')">3</button>
                    <button @click="appendToDisplay('-')">-</button>
    
                    <button @click="appendToDisplay('0')">0</button>
                    <button @click="appendToDisplay('.')">.</button>
                    <button @click="calculate()">=</button>
                    <button @click="appendToDisplay('+')">+</button>
                    
                </div>
                <button @click="clearDisplay" class="clear" :class="clear-button">C</button>
            </div>


        </div>
        

    </div>
</template>

<script>
import { ref, computed} from 'vue'
    export default {
        name: 'AmazingCalculator',
        setup() {
            const display = ref('0');
            const clear = ref ('');
            const button = ref('')

            const appendToDisplay = (value) => {
                if(display.value == '0' && value !== '.') {
                    display.value = value

                }else {
                    display.value += value ;
                }
            }

            const calculate = () => {
                try {
                    display.value = eval(display.value).toString()
                    
                } catch (error) {
                    display.value = 'error'
                    
                }
                
            }

            // computed property for dynamic class binding

            const displayClass = computed(() => {
                return display.value.length > 12 ? 'small-text' : ' '
            })

            const clearDisplay = () => {
                display.value = '0'
            }
            return {
                appendToDisplay,
                calculate,
                displayClass,
                display,
                clearDisplay,
                clear,
                button
             }

            
        }
        
    }
</script>

<style scoped>
input {
    padding: 10px 20px;
    margin-bottom: 20px;
  }

  .main-calc {
    max-width: 600px;
    border: 1px solid #ccc;
    margin: 0 auto;
    padding: 20px;
    background-image: linear-gradient(#335C81, #FFFFFF);
    border-radius: 8px;
  }
  
  .calculator {
    max-width: 400px;
    margin: 50px auto;
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background: grey;
  }
  
  .display {
    width: 100%;
    margin-bottom: 10px;
    padding: 10px;
    font-size: 24px;
    text-align: right;
  }
  
  .buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
  }
  
  button {
    width: 100%;
    padding: 10px;
    font-size: 18px;
  }
  
  .clear {
    width: 100%;
    margin-top: 10px;
  }
  
  .small-text {
    font-size: 20px;
  }
  
  h1 {
    font-style: italic;
    text-align: center;
    color: #ccc;

  }

</style>