<script setup>
import { defineProps } from 'vue';

defineProps(
    {
        bg: {
            type: String,
            default: 'bg-gray-100'
        }
    }
);
</script>

<template>
    <!-- Uso de JavaScript para adicionar um prop {bg}-->
    <div :class="`${bg} p-6 rounded-lg shadow-md`">
        <slot>

        </slot>
    </div>
</template>