<template>
    <tr class="row" v-if="!header">
        <div class="row__header">
            <p v-for="(column, index) in columns" :key="index">{{ column.name }}</p>
        </div>

        <component :is="element" class="col" v-for="(item, index) in content" :key="index">
            <span v-if="(typeof item === 'number')">{{ item | formatNumber }}</span>
            <span v-else>{{ item }}</span>
        </component>

        <td class="col" v-if="editable">
            <wn-input label="Qty" :action="false" :value="content[editable]" inputType="number" size="small" />
        </td>
    </tr>
    <component v-else :is="element" class="col">
        {{ content.name }}

        <button
            v-if="content.sort"
            class="row__sort"
            @click="$emit('sort', content.sort)"
        >
            <font-awesome-icon
                icon="sort"
            />
        </button>
    </component>
</template>

<script>
import WNInput from '@/components/WNInput'

export default {
    name: 'WNTableRow',
    props: {
        content: {
            type: [Object, String],
            required: true
        },
        editable: {
            type: [String, Number],
            required: false
        },
        header: {
            type: Boolean,
            default: false
        },
        columns: {
            type: Array,
            required: false
        }
    },
    components: {
        'wn-input': WNInput
    },
    computed: {
        element() {
            return this.header ? 'th' : 'td'
        }
    },
    filters: {
        formatNumber(number) {
            let numStr = number.toString();
            let dotIndex = numStr.length - 3;
            numStr = numStr.substring(0, dotIndex) + '.' + numStr.substring(dotIndex);

            for (let i = dotIndex - 3; i > 0; i -= 3) {
                numStr = numStr.substring(0, i) + ',' + numStr.substring(i);
            }

            return numStr;
        }
    }
}
</script>

<style lang="scss" scoped>
$color-darkgray: #4d4d4d;
$color-lightgray: #f2f2f2;
.row {
    display: grid;
    border-bottom: 1px solid $color-lightgray;
    grid-template:  "header col"
                    "header col"
                    "header col"
                    "header col"
                    "header col"
                    "header col"
                    "header col";

    @media (min-width: 768px) {
        display: revert;
    }

    &__header {
        background: $color-darkgray;
        padding: 4px;
        color: white;
        text-align: center;
        grid-area: header;

        & > * {
            padding: 8px 6px;
            margin: 0;
        }

        @media (min-width: 768px) {
            display: none;
        }
    }

    &__sort {
        background: transparent;
        border: none;
        cursor: pointer;
        vertical-align: text-top;
        display: inline-flex;
        align-items: center;
    }
}

.col {
    padding: 8px 6px;
    text-align: center;
    display: block;

    @media (min-width: 768px) {
        display: revert;
    }
}
</style>
