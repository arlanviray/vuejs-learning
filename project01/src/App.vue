<script setup>
import TodoList from './components/TodoList.vue'
import RandomQuoteGenerator from './components/RandomQuoteGenerator.vue'
import CalculatorComponent from './components/CalculatorComponent.vue'
import AccordionComponent from './components/AccordionComponent.vue'
import FormValidation from './components/FormValidation.vue'
import PasswordGenerator from './components/PasswordGenerator.vue'
import ProgressSteps from './components/ProgressSteps.vue'
import DadJokes from './components/DadJokes.vue'
import GithubUserSearch from './components/GithubUserSearch.vue'
import WikiComponent from './components/WikiComponent.vue'

const projectComponents = [
  {
    title: 'Todo List',
    component: TodoList
  },
  {
    title: 'Random Quote Generator',
    component: RandomQuoteGenerator
  },
  {
    title: 'Calculator',
    component: CalculatorComponent
  },
  {
    title: 'Accordion',
    component: AccordionComponent
  },
  {
    title: 'Form Validation',
    component: FormValidation
  },
  {
    title: 'Password Generator',
    component: PasswordGenerator
  },
  {
    title: 'Progress Steps',
    component: ProgressSteps
  },
  {
    title: 'Random Dad Jokes: API (Axios)',
    component: DadJokes
  },
  {
    title: 'Github User Search: API',
    component: GithubUserSearch
  },
  {
    title: 'Wiki: API',
    component: WikiComponent
  }
]
</script>

<template>
  <div class="project" v-for="(project, index) in projectComponents" :key="index">
    <component
      :is="project.component"
      v-bind="{ 'project-title': `(${index + 1}) ${project.title}` }"
    />
  </div>
</template>

<style>
*,
*::before,
*::after {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
}

h1 {
  text-align: center;
  margin-top: 0;
  margin-bottom: 30px;
}

.project {
  border-bottom: 2px solid lightgrey;
  padding: 40px 20px 100px;
}

#app .project:last-child {
  border-bottom: 0;
}
</style>
