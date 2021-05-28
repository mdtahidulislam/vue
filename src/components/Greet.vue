<template>
    <div>
        <h2>Hello {{ name }} a.k.a {{ heroname }}</h2>
    </div>
</template>

<script>
    export default {
        name: 'Greet',
        props: ['name', 'heroname']
    }
</script>

<style scoped>

</style>