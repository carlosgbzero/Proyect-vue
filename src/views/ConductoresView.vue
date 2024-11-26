<template>
    <Table :headers="headers" :content="content" :item-per-page="5" />
</template>

<script setup lang="ts">
    import Table from "@/components/Table.vue";
    const headers: string[] = ['Nombre', 'Edad', 'Carnet', 'Telefono']
    const content = [
      ['Carlos', 21, '03040968981', '58471819'],
      ['Luis', 23, '03040968681', '58471819'],
      ['Amara', 32, '03040968581', '58471819'],
      ['Karel', 21, '03040968421', '58471819'],
      ['Jose', 40, '03040968181', '58471819'],
      ['Maria', 22, '03040968431', '58471819'],
      ['Armando', 42, '03040968281', '58471819'],
      ['Carlos', 21, '03040968981', '58471819'],
      ['Luis', 23, '03040968681', '58471819'],
      ['Amara', 32, '03040968581', '58471819'],

    ]
</script>

<style scoped>

</style>