<template>
    <nav class="sticky bottom-0 z-10 bg-white">
        <ul class="flex items-center justify-around border-t">
            <NavItem
                v-for="(icon, page) in navItems"
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
import { ClockIcon, ListBulletIcon, ChartBarIcon } from '@heroicons/vue/24/outline'
import { PAGE_TIMELINE, PAGE_ACTIVITIES, PAGE_PROGRESS } from '../constants'

const emit = defineEmits(['navigate'])

defineProps(['currentPage'])

const navItems = {
    [PAGE_TIMELINE]: ClockIcon,
    [PAGE_ACTIVITIES]: ListBulletIcon,
    [PAGE_PROGRESS]: ChartBarIcon,
}
</script>

<style lang="scss" scoped></style>
