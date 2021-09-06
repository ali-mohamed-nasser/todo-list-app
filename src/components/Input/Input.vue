<template>
    <div className="input-area">
        <label v-if="mainlabel" className="main-label">{{ mainlabel }}</label>
        <input @input="$emit('input-change', inputValue)" autocomplete="off" @change="$emit('input-change', inputValue)" v-model="inputValue" :type="inputType" :name="name" :placeholder="placeholder"/>
    </div>
</template>

<script>
import './Input.scss';
export default {
    name: 'Input',
    props: {
        mainlabel: String,
        inputType: {
            type: String,
            default: 'text'
        },
        name: String,
        placeholder: String
    },
    data() {
        return {
            inputValue: ''
        }
    },
    emits: ['input-change']
}
</script>
