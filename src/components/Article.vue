<template>
    <div>
        <h2 v-bind="$attrs">this article component</h2>
    </div>
</template>

<script>
    export default {
        name: 'Article',
        inheritAttrs: false,
    }
</script>

<style scoped>

</style>