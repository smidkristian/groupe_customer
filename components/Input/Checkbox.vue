<template>
    <div class="flex w-full">
        <input type="checkbox" class="mr-2 rounded border text-sm" />
        <label class="text-xs text-gray-400">
            {{ label }}
        </label>
    </div>
</template>

<script>
    export default {
        props: {
            label: String
        }
    }
</script>

<style scoped>

</style>
