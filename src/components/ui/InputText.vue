<template>
    <div class="input-text">
        <h4>
            <label :for="name">
                <slot />
                <span v-if="optionnal"> (optionnel)</span>
            </label>
        </h4>
        <input
            v-model="valueModel"
            :name="name"
            :id="name"
            :type="type"
            :accept="accept"
        />
    </div>
</template>

<script>
export default {
    name: 'InputText',
    props: {
        name: {
            type: String,
            required: true,
        },
        value: {
            type: String,
            required: true,
        },
        optionnal: {
            type: Boolean,
            default: false,
        },
        type: {
            type: String,
            default: 'text',
        },
        accept: {
            type: String,
            default: '*',
        },
    },
    computed: {
        valueModel: {
            get: function() {
                return this.value
            },
            set: function(val) {
                this.$emit('input', val)
            },
        },
    },
}
</script>

<style lang="scss" scoped>
.input-text {
    width: 100%;
}
input {
    width: 100%;
    border: #42b983 1px solid;
    border-radius: 12px;
    padding: 5px;
}
</style>
