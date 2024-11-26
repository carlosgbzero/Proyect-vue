<template>
    <div class="actions">
        <CFormInput 
          type="text"
          class="searchBar"       
          placeholder="Buscar"
          v-model="searchText"
          @input="onSearch"> 
        </CFormInput>
          <CButton color="primary" class="action-button">Agregar</CButton>
          <CButton color="warning" class="action-button">Modificar</CButton>
          <CButton color="danger" class="action-button">Eliminar</CButton>
    </div>
</template>

<script setup lang="ts">
import { CButton, CFormInput,  } from '@coreui/vue';
import { ref } from 'vue';

const searchText = ref('')

const emit = defineEmits(['search']);
function onSearch(){
    emit('search', searchText.value)
}
</script>

<style scoped>
    .actions{
        display: flex;
        align-items: center;
        gap: 0.5rem;
        flex-wrap: wrap;
    }

    .searchBar{
        flex: 1;
        padding: 0.5rem;
        border-radius: 4px;
        border: 1px solid #ccc;
        
    }

    @media screen and (max-width: 600) {
        .searchBar{
            font-size: large;
        }
    }
</style>