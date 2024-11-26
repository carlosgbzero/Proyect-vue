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
  
  <script lang="ts">
  import { CForm, CFormLabel, CFormInput, CButton } from "@coreui/vue";
  
  export default {
    components: {
      CForm,
      CFormLabel,
      CFormInput,
      CButton,
    },
    data() {
      return {
        username: "",
        password: "",
      };
    },
    methods: {
      onSubmit() {
        console.log("Usuario:", this.username);
        console.log("Contraseña:", this.password);
      },
    },
  };
  </script>
  
  <style>
  </style>