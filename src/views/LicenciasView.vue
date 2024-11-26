<template>
    <Table :headers="headers" :content="content" :item-per-page="5"/>
</template>

<script setup lang="ts">
    import Table from "@/components/Table.vue";
    const headers: string[] = ['ID', 'Tipo', 'Fecha Emision']
    const content = [
    ['03040968981', 'A1','12/05/2016'],
      ['03040968681', 'A','12/05/2016'],
      ['03040968581', 'C1','12/05/2016'],
      ['03040968421', 'B','12/05/2016'],
      ['03040968181', 'F','12/05/2016'],
      ['03040968431', 'B','12/05/2016'],
      ['03040968281', 'A','12/05/2016'],
    ]
</script>

<style scoped>

</style>