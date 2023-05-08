<script setup>
const props = defineProps({
    conversations: {
        type: [Array],
        required: true,
    }
})
</script>

<template>
    <div class="h-full w-full px-3 overflow-y-auto">
        <div v-for="conversation in conversations">
            <div v-if="conversation.nameSender === 'Mohammed'" class="w-full flex justify-end">
                <div class="bg-blue-300 my-3 max-w-full w-fit px-2 rounded-2xl py-1">
                    <p>{{ conversation.mes }}</p>
                </div>
            </div>
            <div v-if="conversation.nameSender === 'Ali'" class="w-full flex justify-start">
                <div class="bg-gray-400 my-3 max-w-full w-fit px-2 rounded-2xl py-1">
                    <p>{{ conversation.mes }}</p>
                </div>
            </div>
        </div>

    </div>
</template>
