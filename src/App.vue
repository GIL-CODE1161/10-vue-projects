<template>
  <div>
    <TodoList/>,
    <RandomQuoteGenerator/>
    <AmazingCalculator/>
    <Accordion/>
    <FormValidation/>
    <PasswordGenerator/>
    <ProgressSteps/>
    <DadJokes/>
    <GithubUsersSearch/>
    <WikiClone/>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue'
import RandomQuoteGenerator from './components/RandomQuoteGenerator.vue'
import AmazingCalculator from './components/AmazingCalculator.vue'
import Accordion from './components/Accordion.vue';
import FormValidation from './components/FormValidation.vue'
import PasswordGenerator from './components/PasswordGenerator.vue';
import ProgressSteps from './components/ProgressSteps.vue';
import DadJokes from './components/DadJokes.vue';
import GithubUsersSearch from './components/GithubUsersSearch.vue'
import WikiClone from './components/WikiClone.vue'
  export default {
    components: {
      
      TodoList,
      RandomQuoteGenerator,
      AmazingCalculator,
      Accordion,
      FormValidation,
      PasswordGenerator,
      ProgressSteps,
      DadJokes,
      GithubUsersSearch,
      WikiClone
    },
    name: 'App'
  }
</script>

<style  scoped>
:root {
  background-color: black;
}

</style>