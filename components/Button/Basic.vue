<template>
    <button :type="type" class="rounded bg-blue-400 px-4 py-1 text-white text-sm hover:bg-blue-600 focus:outline-none">
        <slot></slot>
    </button>
</template>

<script>
    export default {
        props: {
            type: String
        }
    }
</script>

<style scoped>

</style>
