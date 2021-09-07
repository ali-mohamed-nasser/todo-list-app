<template>
    <button @click="$emit('button-clicked')" :class="className"><slot /></button>
</template>

<script>
import './Button.scss';
export default {
    name: 'Button',
    props: {
        className: String
    },
    emits: ['button-clicked']
}
</script>
