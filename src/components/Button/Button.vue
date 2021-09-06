<template>
    <button :class="className"><slot /></button>
</template>

<script>
import './Button.scss';
export default {
    name: 'Button',
    props: {
        className: String
    }
}
</script>
