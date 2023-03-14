<template>
    <div class="flex items-center hover:bg-gray-100 rounded-md w-full py-1.5 px-2">
        <img 
            v-if="user.image"
            class="rounded-full lg:mx-0 mx-auto" 
            width="35" 
            :src="user.image"
        >
        <div class="lg:pl-2.5 lg:block hidden">
            <div class="flex items-center">
                <div class="font-bold text-[14px]">
                    {{ $generalStore.allLowerCaseNoCaps(user.name) }}
                </div>
                <div class="ml-1 rounded-full bg-[#58D5EC] h-[14px] relative">
                    <Icon class="relative -top-[7px]" name="teenyicons:tick-small-solid" color="#FFFFFF" size="15"/>
                </div>
            </div>

            <div class="font-light text-[12px] text-gray-600">
                {{ user.name }}
            </div>
        </div>
    </div>
</template>

<script setup>
const { $generalStore } = useNuxtApp()
defineProps(['user'])
</script>