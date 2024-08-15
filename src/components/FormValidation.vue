<template>
    <div>
        <div class="form">
            <h1>Form Validation</h1>
        <form @submit.prevent="submitForm" class="custom-form">
            <div class="form-group">
                <label for="name">Name: </label>
                <input v-model="formData.name" type="text"  id="name">
                <span class="error" v-if="!isNameValid">Name is required</span>

            </div>
            <div class="form-group">
                <label for="email">Email: </label>
                <input v-model="formData.email" type="email"  id="email">
                <span class="error" v-if="!isEmailValid">Please enter a valid email address</span>

            </div>
            <div class="form-group">
                <label for="password">Password: </label>
                <input v-model="formData.password" type="text"  id="password">
                <span class="error" v-if="!isPasswordValid">Invalid Password! Password must be at least 8 characters</span>

            </div>
            <button type="submit"  :disabled="!isFormValid" class="submit-button">Submit</button>

        </form>
    </div>

    </div>
</template>

<script>
import { computed, ref } from 'vue'
    export default {
        name: 'FormValidation',

        setup() {
            const formData = ref({
                name: "",
                email: " ",
                password: " "

            })

            const isNameValid = computed(() => formData.value.name.trim() !== '')
            const isEmailValid = computed(() =>  /^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(formData.value.email))
            const isPasswordValid = computed(() =>  formData.value.password.length >= 8)
            const isFormValid = computed(() => isNameValid.value && isEmailValid.value && isPasswordValid.value)

            const submitForm =() => {
                if (isFormValid.value) {
                    console.log ("Submitted successfully", formData.value)
                } else {
                    alert ("Invalid inputs! Please check the fields")
                }
            }

            return {
                submitForm,
                isEmailValid,
                isNameValid,
                isPasswordValid,
                formData,
                isFormValid

            }
            
        }
    }
</script>

<style scoped>
.form {
border: 1px solid #ccc;
max-width: 540px;
margin: 50px auto;
padding: 50px;
background-image: linear-gradient(#F7D4D4, #F6ECC4 );
border-radius: 8px;

}
.custom-form {
    max-width: 400px;
    margin: 0 auto;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
  }
  
  input {
    width: 100%;
    padding: 10px;
    font-size: 16px;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .error {
    color: #e74c3c;
    font-size: 14px;
    margin-top: 5px;
  }
  
  .submit-button {
    padding: 10px 15px;
    font-size: 16px;
    background-color: #3498db;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  .submit-button:disabled {
    background-color: #5e6468;
    cursor: not-allowed;
  }
  h1 {
    color: black;
    text-align: center;
    font-style: italic;
  }

</style>