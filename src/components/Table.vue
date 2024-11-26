<template>
    <div class="table-responsive">
      <!--------Tabla-------->
      <CTable hover bordered striped class="table">
        <CTableHead>
          <CTableRow>
            <CTableHeaderCell v-for="(header, index) in prop.headers" :key="index">
              {{ header }}
            </CTableHeaderCell>
          </CTableRow>
        </CTableHead>
        <CTableBody>
          <CTableRow v-for="(row, rowIndex) in paginatedContent" :key="rowIndex">
            <CTableDataCell v-for="(cell, cellIndex) in row" :key="cellIndex">
              {{ cell }}
            </CTableDataCell>
          </CTableRow>
        </CTableBody>
      </CTable>
    <!--------Paginacion-------->
    <div class="pagination">
      <CButton :disabled="currentPage === 1" @click="prevPage" class="pBtn">Anterior</CButton>
      <span style="align-content: center;">{{ currentPage }} de {{ totalPages }}</span>
      <CButton :disabled="currentPage === totalPages" @click="nextPage" class="pBtn">Siguiente</CButton>
    </div>
    </div>
  </template>
  
  <script lang="ts" setup>
  import {
    CTable,
    CTableHead,
    CTableBody,
    CTableRow,
    CTableHeaderCell,
    CTableDataCell,
    CButton,
  } from "@coreui/vue";
import { computed, ref } from "vue";

  interface Props {
    headers: string[];
    content: Record<string,any>[];
    itemPerPage: number;
    filterText?: string;
  }
  const prop = defineProps<Props>();

  const currentPage = ref<number>(1);
  const itemPerPage = ref<number>(prop.itemPerPage);

  const totalPages = computed(() => Math.ceil(prop.content.length / itemPerPage.value));

  const filteredContent = computed(() => {
    const search = prop.filterText?.toLowerCase() || '';
    return prop.content.filter( (row) => Object.values(row).some((value) => 
    String(value).toLowerCase().includes(search)))
  })

  const paginatedContent = computed(() => {
    const start = (currentPage.value - 1) * itemPerPage.value;
    const end = start + itemPerPage.value;
    return filteredContent.value.slice(start, end);
  })

  function prevPage(){
    if(currentPage.value > 1)
      currentPage.value--;
  }

  function nextPage(){
    if(currentPage.value < totalPages.value)
      currentPage.value++;
  }
  
  </script>
  
  <style>
  .table-responsive {
    overflow-x: auto;
    border-radius: 8px;
  }

  .table{
    width: 100%;
    margin-bottom: 0;
  }

  .pagination{
    display: flex;
    justify-content: center;
    margin-top: 1rem;
  }

  .pBtn{
    margin: 0 0.5rem;
    padding: 0.5rem 1rem;
    cursor: pointer;
  }
  </style>