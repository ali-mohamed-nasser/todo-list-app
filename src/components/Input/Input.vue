<template>
    <div className="input-area">
        <label v-if="mainlabel" className="main-label">{{ mainlabel }}</label>
        <input autocomplete="off" :value="modelValue" :checked="checked" @input="$emit('update:modelValue', $event.target.value)" :type="inputType" :name="name" :placeholder="placeholder"/>
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
        placeholder: String,
        modelValue: [String, Boolean],
        checked: [String, Boolean]
    },
    emits: ['update:modelValue']
}
</script>
