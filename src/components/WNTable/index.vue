<template>
    <div>
        <div class="table__filter">
            <wn-input
                placeholder="Product search"
                v-model="model"
            />
        </div>

        <table class="table">
            <thead class="table__head">
                <wn-table-row
                    v-for="(col, index) in cols"
                    :key="index"
                    :content="col"
                    :header="true"
                ></wn-table-row>
            </thead>
            <tbody class="table__body">
                <wn-table-row
                    v-for="(row, index) in rows"
                    :key="index"
                    :content="row"
                    editable="available"
                ></wn-table-row>
            </tbody>
        </table>
    </div>
</template>

<script>
import WNInput from '@/components/WNInput'
import WNTableRow from './WNTableRow.vue';

export default {
    name: 'WNTable',

    props: {
        cols: {
            type: Array,
            required: true
        },
        rows: {
            type: Array,
            required: true
        }
    },

    data() {
        return {
            model: ''
        }
    },

    components: {
        'wn-input': WNInput,
        'wn-table-row': WNTableRow
    }
}
</script>

<style lang="scss" scoped>
    $color-lightgray: #f2f2f2;
    .table {
        table-layout: fixed;
        border-collapse: collapse;
        font-size: 12px;
        width: 100%;

        &__head {
            background: $color-lightgray;
        }

        &__filter {
            margin-bottom: 1em;
            max-width: 180px;
        }
    }
</style>
