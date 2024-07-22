<script setup>
import TodoList from './components/TodoList.vue'
import RandomQuoteGenerator from './components/RandomQuoteGenerator.vue'
import AmazingCalculator from './components/AmazingCalculator.vue'
import AccordionComponent from './components/AccordionComponent.vue'
import FormValidation from './components/FormValidation.vue'
import PasswordGenerator from './components/PasswordGenerator.vue'
import ProgressSteps from './components/ProgressSteps.vue'

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
    component: AmazingCalculator
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
body {
  margin: 0;
  padding: 0;
}

h1 {
  text-align: center;
  margin-top: 0;
}

.project {
  border-bottom: 2px solid lightgrey;
  padding: 40px 20px;
}

#app .project:last-child {
  border-bottom: 0;
  padding-bottom: 100px;
}
</style>
