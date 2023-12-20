<template>
    <label>
        <input
            class="input"
            :type="inputType"
            :placeholder="placeholder"
            @input="onInput"
        />
        <button class="input__action" v-if="action" @click="$emit('sea')">
            <font-awesome-icon
                v-if="inputType === 'search'"
                icon="magnifying-glass"
            />
        </button>
    </label>
</template>

<script>
export default {
    name: 'WNInput',

    props: {
        placeholder: {
            type: String,
            default: 'Type Here'
        },
        inputType: {
            type: String,
            default: 'search'
        },
        action: {
            type: Boolean,
            default: true
        }
    },

    data() {
        return {
            error: ''
        }
    },

    methods: {
        onInput(event) {
            const value = event.target.value;

            if (!value) {
                this.error = 'Value should not be empty';
            }

            this.$emit('input', event.target.value)
        }
    }
}
</script>

<style lang="scss" scoped>
    $color-gray: #bfbfbf;
    $color-lightgray: #f2f2f2;

    %input {
        padding: 4px 6px;
        outline: none;
        border: 1px solid $color-gray;
    }


    .input {
        @extend %input;
        border-top-left-radius: 4px;
        border-bottom-left-radius: 4px;

        &__action {
            @extend %input;
            background: $color-lightgray;
            cursor: pointer;
            border-left: none;
            border-top-right-radius: 4px;
            border-bottom-right-radius: 4px;

            svg {
                vertical-align: middle;
            }
        }
    }
</style>
