<template>
    <label class="input__wrapper" :class="{ 'input__wrapper--small': size === 'small' }">
        <span v-if="label" class="input__label">{{ label }}</span>
        <input
            class="input"
            :class="{ 'input--labeled': label && label.length }"
            :value="value"
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
        },
        label: {
            type: String,
            required: false
        },
        value: {
            type: [String, Number],
            required: false
        },
        size: {
            type: String,
            required: false
        }
    },

    data() {
        return {
            error: ''
        }
    },

    methods: {
        onInput(event) {
            const value = event.target.value

            if (!value) {
                this.error = 'Value should not be empty'
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
        width: 100%;

        &--labeled {
            border-top-left-radius: 0;
            border-bottom-left-radius: 0;
            border-top-right-radius: 4px;
            border-bottom-right-radius: 4px;
        }

        &__wrapper {
            display: flex;
            align-items: center;

            &--small {
                .input {
                    font-size: 10px;
                    line-height: 12px;
                }
            }
        }

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

        &__label {
            @extend %input;
            background: $color-lightgray;
            font-size: 14px;
            border-top-left-radius: 4px;
            border-bottom-left-radius: 4px;
            line-height: 12px;
            font-size: 10px;
        }
    }
</style>
