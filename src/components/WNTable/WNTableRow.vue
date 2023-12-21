<template>
    <tr class="row" v-if="(typeof content === 'object')">
        <component :is="element" class="col" v-for="(item, index) in content" :key="index">
            {{ item }}
        </component>

        <td class="col" v-if="editable">
            <wn-input
                label="Qty"
                :action="false"
                :value="content[editable]"
                inputType="number"
                size="small"
            />
        </td>
    </tr>
    <component :is="element" class="col" v-else>
        {{ content }}
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
        }
    },
    components: {
        'wn-input': WNInput
    },
    computed: {
        element() {
            return this.header ? 'th' : 'td'
        }
    }
}
</script>

<style lang="scss" scoped>
    .col {
        padding: 8px 0;
        text-align: center;
    }
</style>
