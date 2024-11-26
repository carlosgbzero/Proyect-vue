<template>
    <div class="container">
      <NavBar v-on:update-view="changeView"/> 
      <div class="container-content">
        <section class="info">
          <div class="card">
            <h4>Lorem ipsum dolor sit amet consectetur adipisicing elit. Consequuntur dolore, soluta, voluptatem explicabo </h4>
          </div>
          <div class="card">
            <h4>Lorem ipsum dolor sit amet consectetur adipisicing elit.</h4>
          </div>
        </section>
        <hr>
        <Actions @search="updateFilterText"/>
        <hr>
       <component :is="currentView" :filterText="filterText"/>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">

    import { computed, ref } from 'vue';
    import NavBar from "@/components/NavBar.vue";
    import Actions from "@/components/Actions.vue";
    import ConductoresView from "@/views/ConductoresView.vue";
    import LicenciasView from './LicenciasView.vue';
    import InfraccionesView from './InfraccionesView.vue';
    import ExamenesMView from './ExamenesMView.vue';
    import ExamenesTView from './ExamenesTView.vue';
    import ExamenesPView from './ExamenesPView.vue';

    const filterText= ref('');

    function updateFilterText(text:string){
      filterText.value = text
    }
    
    const currentView = ref(ConductoresView)
    const views = {
      condutores : ConductoresView,
      licencias : LicenciasView,
      examenesM : ExamenesMView,
      examenesT : ExamenesTView,
      examenesP : ExamenesPView,
      infracciones : InfraccionesView
    }

    function changeView(view: string){
      if(view.match("ConductoresView"))
          currentView.value = views.condutores
      else if(view.match("LicenciasView"))
          currentView.value = views.licencias
      else if(view.match("ExamenesMView"))
          currentView.value = views.examenesM
      else if(view.match("ExamenesTView"))
          currentView.value = views.examenesT
      else if(view.match("ExamenesPView"))
          currentView.value = views.examenesP
      else if(view.match("InfraccionesView"))
          currentView.value = views.infracciones
    }
  </script>
  
  <style lang="css" scoped>
  
    body{
      background-color: #212529;
      color: #f8f9fa;
      overflow: hidden;
    }
  
    .container{
      margin-left: 250px;
      display: flex;
      height: 100vh;
      padding: 0%;
      overflow: hidden;
    }  
    .container-content{  
      flex: 1;
      margin-right: 40px;
      display: flex;
      flex-direction: column;
      padding: 1rem;
      overflow: hidden;
    }
  
    .info{
      display: flex;
      align-content: center;
      background-color: #f9f9f9;
      padding: 1rem;
      border: 1px, solid, #ddd;
      margin-bottom: 1rem;
    }
  
    .card{
      margin-left: 1rem;
    }
    .actions{
      display: flex;
      align-content: center;
      flex-wrap: nowrap;
      gap: 0.5rem;
  
    }
    
    #searchBar{
      flex: 1;
      padding: 0.5rem;
      margin-right: 1rem;
      border: 1px, solid, #ddd;
      border-radius: 4px;
    }
  
    .action-button{
      padding: 0.5rem 1rem;
      margin-left: 0.5rem;
      border: none;
      border-radius: 4px;
      cursor: pointer;
    }
  
    .table-section {
      flex: 1;
      border-radius: 8px;
      overflow-x: auto;
    }
  
  </style>