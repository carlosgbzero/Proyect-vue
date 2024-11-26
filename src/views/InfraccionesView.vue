<template>
    <Table :headers="headers" :content="content" :item-per-page="5"/>
</template>

<script setup lang="ts">
    import Table from "@/components/Table.vue";
    const headers: string[] = ['ID', 'Gravedad', 'Fecha Examen']
    const content = [
    
    [ '03040968981', 'Leve', '22/04/2016'],
    ['03040968681','Grave', '22/04/2016'],
    [ '03040968581', 'Leve', '22/04/2016'],
    [ '03040968421', 'Leve', '22/04/2016'],
    ['03040968181','Muy Grave', '22/04/2016'],
]  
</script>

<style scoped>

</style>