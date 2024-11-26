<template>
    <!-- Contenedor del Modal -->
    <div v-if="isOpen" class="modal-overlay">
      <div class="modal-content">
        <div class="modal-header">
          <h2>{{ title }}</h2>
          <button @click="closeModal" class="close-btn">X</button>
        </div>
  
        <!-- Inputs dinámicos -->
        <form @submit.prevent="submitForm">
          <div class="modal-body">
            <div v-for="(input, index) in inputs" :key="index" class="form-group">
              <label :for="'input-' + index">{{ input.label }}</label>
              <input
                v-model="formData[index]"
                :type="input.type"
                :id="'input-' + index"
                :placeholder="'Ingrese ' + input.label"
              />
            </div>
          </div>
  
          <div class="modal-footer">
            <button type="submit">Guardar</button>
            <button type="button" @click="closeModal">Cancelar</button>
          </div>
        </form>
      </div>
    </div>
  </template>
  
  <script setup lang="ts">
  import { defineProps, defineEmits, ref } from 'vue';
  
  // Interfaz para los inputs
  interface InputField {
    label: string;
    type: string; // Puede ser 'text', 'date', 'number', etc.
  }
  
  // Props
  const props = defineProps<{
    isOpen: boolean;
    title: string;
    inputs: InputField[]; // Tipamos la propiedad inputs como un array de InputField
  }>();
  
  const emit = defineEmits(['close', 'submit']);
  
  // Estado del formulario
  const formData = ref<string[]>(new Array(props.inputs.length).fill(''));
  
  // Métodos
  function closeModal() {
    emit('close'); // Emitir el evento para cerrar el modal
  }
  
  function submitForm() {
    emit('submit', formData.value); // Emitir el formulario con los datos
  }
  </script>
  
  <style scoped>
  .modal-overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .modal-content {
    background: white;
    padding: 20px;
    border-radius: 10px;
    width: 400px;
  }
  
  .modal-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  
  .close-btn {
    background: none;
    border: none;
    font-size: 20px;
    cursor: pointer;
  }
  
  .modal-body {
    margin-top: 10px;
  }

  .form-group{
    margin-bottom: 10px;
  }

  .modal-footer{
    display: flex;
    justify-content: space-between;
    margin-top: 20px;
  }
  
</style>