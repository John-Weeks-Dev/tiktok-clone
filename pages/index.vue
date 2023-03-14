<template>
    <MainLayout>
        <div class="pt-[80px] w-[calc(100%-90px)] max-w-[690px]">
            <div v-for="post in $generalStore.posts" :key="post">
                <PostMain v-if="post" :post="post" />
            </div>
        </div>
    </MainLayout>
</template>

<script setup>
import MainLayout from '~/layouts/MainLayout.vue';
const { $generalStore } = useNuxtApp()
onMounted(async () => {
    try {
        $generalStore.getAllUsersAndPosts()
    } catch (error) {
        console.log(error)
    }
})
</script>
