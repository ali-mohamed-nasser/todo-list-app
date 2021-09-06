<template>
    <button @click="onClickTest" :class="className"><slot /></button>
</template>

<script>
import './Button.scss';
export default {
    name: 'Button',
    props: {
        className: String
    },
    methods: {
        onClickTest() {
            console.log('click testing');
        }
    }
}
</script>
