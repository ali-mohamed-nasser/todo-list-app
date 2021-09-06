<template>
    <div className="input-area">
        <label v-if="mainlabel" className="main-label">{{ mainlabel }}</label>
        <input :type="inputType" :name="name" :placeholder="placeholder"/>
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
    }
}
</script>
