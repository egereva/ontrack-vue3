<template>
    <nav class="sticky bottom-0 z-10 bg-white">
        <ul class="flex items-center justify-around border-t">
            <NavItem
                v-for="(icon, page) in NAV_ITEMS"
                :key="page"
                :href="`#${page}`"
                @click="emit('navigate', page)"
                :class="{ 'bg-gray-200 pointer-events-none': currentPage === page }"
            >
                <component :is="icon" class="h-6 w-6"></component> {{ page }}
            </NavItem>
        </ul>
    </nav>
</template>

<script setup>
import NavItem from './NavItem.vue'
import { NAV_ITEMS } from '../constants'

const emit = defineEmits(['navigate'])

defineProps({
    currentPage: {
        type: String,
        required: true,
    },
})
</script>

<style lang="scss" scoped></style>
