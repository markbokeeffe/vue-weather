<template>
    <div>
        <label>{{ label }}</label>
        <select v-model="value" v-on:change="this.updateSelect">
            <option v-for="option in options" :key="option" :value="option">{{option}}</option>
        </select>
    </div>
</template>


<script>
    export default {
        name: 'SelectDropdown',
        props: {
            options: Array,
            onChange: Function,
            model: String,
            label: String
        },
        data () {
            return {
                value: this.options[0]
            }
        },
        methods: {
            updateSelect: function() {
                this.$emit("updateLocation", this.value);
            }
        }
    }
</script>

<style>
    label {
        font-size: 15px;
        margin-right: 10px;
    }
    select {
        font-size: 15px;
    }
</style>