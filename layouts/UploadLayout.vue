<template>
    <div class="bg-[#F8F8F8] h-[100vh]">
        <TopNav/>
        <div class="flex justify-between mx-auto w-full px-2 max-w-[1140px]">
            <slot />
        </div>
    </div>
</template>

<script setup>
const route = useRoute()
</script>
