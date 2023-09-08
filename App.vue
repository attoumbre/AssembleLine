<template>
    <div id="vue-app">
      <AssemblyLine :stages='[
          "Idea", 
          "Development", 
          "Testing", 
          "Deployment"
        ]' 
      />
    </div>
  </template>
  
  <script>
  import AssemblyLine from './components/AssemblyLine.vue'
  
  export default {
      name: 'vue-app',
      computed: {
      },
      components: {
          AssemblyLine
      }
  }
  </script>
  
  <style>
  #vue-app {
    font-family: arial;
  }
  
  .example {
    padding: 1rem;
    background-color: #f8f8f8;
    margin-bottom: 1rem;
  }
  .h2 {
      margin-top: 0;
      font-size: 16px;
    }
  </style>