<template>
    <div>
        <h2>ComponentF</h2>
        <h2>componentF username - {{ username }}</h2>
    </div>
</template>

<script>
    export default {
        name: 'ComponentF',
        inject: ['username']
    }
</script>

<style scoped>

</style>