<template>
    <Table :headers="headers" :content="content" :item-per-page="5"/>
</template>

<script setup lang="ts">
    import Table from "@/components/Table.vue";
    const headers: string[] = ['ID', 'Resultado', 'Fecha Examen']
    const content = [
    
    [ '03040968981', 'Aprobado', '22/04/2016'],
    ['03040968681','Aprobado', '22/04/2016'],
    [ '03040968581', 'Suspenso', '22/04/2016'],
    [ '03040968421' , 'Aprobado', '22/04/2016'],
    ['03040968181','Aprobado', '22/04/2016'],
    [ '03040968431', 'Suspenso', '22/04/2016'],
    [, '03040968281','Aprobado', '22/04/2016'],
]  
</script>

<style scoped>

</style>