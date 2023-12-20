<template>
    <div>
        <wn-input
            placeholder="Product search"
            v-model="model"
        />

        <table>

        </table>
    </div>
</template>

<script>
import WNInput from '@/components/WNInput'

export default {
    name: 'WNTable',

    data() {
        return {
            model: ''
        }
    },

    components: {
        'wn-input': WNInput
    }
}
</script>
