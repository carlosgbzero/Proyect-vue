<template>
      <CNavbar expand="md" class="flex-column vh-100 bg-primary text-light" id="navB" >
        <div class="p-3">
            <hr>
            <h2 class="text-center mb-4 mt-4">SysGL</h2>
            <RouterLink to="/" style="color: rgb(255, 255, 255); text-decoration: underline;">
              Cerrar Sesión
            </RouterLink>
            <hr>
        </div>
        <CNav vertical class="flex-column">
          <CNavItem>
            <CButton  color="primary" class="w-100" style="margin-bottom: 10px;" @click="selectOption(1),
             changeView('ConductoresView')">Conductores</CButton>
          </CNavItem>
          <CNavItem>
            <CButton  color="primary" class="w-100" style="margin-bottom: 10px;" @click="selectOption(2),
            changeView('LicenciasView')">Licencias</CButton>
          </CNavItem>
          <CNavItem>
            <CButton  color="primary" class="w-100" style="margin-bottom: 10px;" @click="toggleExams()"> {{ exam }} </CButton>
          </CNavItem>
          <div v-if="showExams" class="ms-4">
            <CNavItem>
            <CButton  color="primary" class="w-100" style="margin-bottom: 10px;" @click="changeView('ExamenesMView')">Medicos</CButton>
            </CNavItem>
            <CNavItem>
            <CButton  color="primary" class="w-100" style="margin-bottom: 10px;" @click="changeView('ExamenesTView')">Teoricos</CButton>
            </CNavItem>
            <CNavItem>
            <CButton  color="primary" class="w-100" style="margin-bottom: 10px;" @click="changeView('ExamenesPView')">Practicos</CButton>
            </CNavItem>
          </div>
          <CNavItem>
            <CButton  color="primary" class="w-100" style="margin-bottom: 10px;" @click="selectOption(6), changeView('InfraccionesView')" >Infracciones</CButton>
          </CNavItem>
        </CNav>
      </CNavbar>
  </template>
  
  <script setup lang="ts">
  import LoginView from "@/views/LoginView.vue";
import {
    CNavbar,
    CNav,
    CNavItem,
    CButton,
  } from "@coreui/vue";
    import { ref, defineEmits } from "vue";
    import { RouterLink } from "vue-router";

  const showExams = ref(false) // controla la visibilidad de los tipos de examenes
  const exam = ref("Examenes ⋎")
  const toggleExams = () => {
    showExams.value = !showExams.value
    if(showExams.value)
        exam.value = "Examenes ⋏"
    else
        exam.value = "Examenes ⋎"
  }

  const selectOption = (option: number) => {
    console.log(option)
    showExams.value = false
    exam.value = "Examenes ⋎"
  }

  const emit = defineEmits(['update-view'])

  function changeView(view: string){
    emit('update-view',view)
  }
  </script>
  
  <style lang="css" scoped>
    #navB{
        width: 250px;
        padding: 1rem 0; 
        display: flex;
        position: fixed; 
        top: 0;
        bottom: 0; 
        left: 0;
        flex-shrink: 0;
    }

    @media only screen and (max-width: 600) {
        #navB{
            width: 100;
        }   
    }

  </style>