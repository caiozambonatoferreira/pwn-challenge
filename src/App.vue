<template>
  <div class="container">
    <h2 class="subtitle">Inventory</h2>

    <wn-table
        :columns="products"
    />
  </div>
</template>

<script>
import WNTable from '@/components/WNTable'

export default {
    name: 'App',

    components: {
       'wn-table': WNTable
    },

    data() {
        return {
            products: [
                {
                    code: 'ACC1',
                    name: 'Apple granny smith',
                    package: '40 LB',
                    available: 3638066,
                    category: 'Fruits',
                    last_updated: '2021-02-05 08:28:36'
                },
                {
                    code: 'ACC1',
                    name: 'Pineapple crownless',
                    package: '7 CT',
                    available: 6462020,
                    category: 'Fruits',
                    last_updated: '2021-02-03 19:49:33'
                },
            ]
        }
    }
}
</script>

<style lang="scss">
$color-dark: #333333;

* {
    font-family: sans-serif;
}

.container {
    max-width: 1140px;
    margin: 0 auto;
}

.subtitle {
    color: $color-dark;
}
</style>
