<template>
    <div class="d-flex justify-content-center align-items-center vh-100 bg-primary">
      <div class="card p-4 shadow-sm" style="width: 400px;">
        <h2 class="text-center mb-4">Iniciar Sesión</h2>
        <CForm @submit.prevent="onSubmit">
          <div class="mb-3">
            <CFormLabel for="username">Nombre de Usuario</CFormLabel>
            <CFormInput
              type="text"
              id="username"
              v-model="username"
              placeholder="Ingresa tu usuario"
              required
            />
          </div>
          <div class="mb-3">
            <CFormLabel for="password">Contraseña</CFormLabel>
            <CFormInput
              type="password"
              id="password"
              v-model="password"
              placeholder="Ingresa tu contraseña"
              required
            />
          </div>
          <CButton type="submit" color="primary" class="w-100">
            Iniciar
          </CButton>
        </CForm>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { CForm, CFormLabel, CFormInput, CButton } from "@coreui/vue";
  import { defineEmits, ref } from "vue";
  import { useRouter } from "vue-router";

  const username = ref('');
  const password = ref('');
  const router = useRouter();
  

  function onSubmit() {
        console.log("Usuario:", username.value);
        console.log("Contraseña:", password.value);
        router.push('/main')
      }
  </script>
  
  <style>
  </style>