<template>
    <NuxtPage />

    <AuthOverlay v-if="isLoginOpen" />
    <EditProfileOverlay v-if="isEditProfileOpen" />
</template>

<script setup>
import { storeToRefs } from 'pinia';
const { $userStore, $generalStore } = useNuxtApp()
const { isLoginOpen, isEditProfileOpen } = storeToRefs($generalStore)

onMounted(async () => {
    $generalStore.bodySwitch(false) 
    isLoginOpen.value = false
    isEditProfileOpen.value = false

    try {
        await $generalStore.hasSessionExpired()
        await $generalStore.getRandomUsers('suggested')
        await $generalStore.getRandomUsers('following')

        if ($userStore.id) {
            $userStore.getUser()
        }
    } catch (error) {
        console.log(error)
    }
})

watch(() => isLoginOpen.value, (val) => $generalStore.bodySwitch(val) )
watch(() => isEditProfileOpen.value, (val) => $generalStore.bodySwitch(val) )
</script>
