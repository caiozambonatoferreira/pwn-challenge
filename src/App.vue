<template>
  <div class="container">
    <h2 class="subtitle">Inventory</h2>

    <wn-table
        :cols="labels"
        :rows="products"
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
            labels: [
                { name: 'Item code' },
                { name: 'Product', sort: 'name' },
                { name: 'Package' },
                { name: 'Available units', sort: 'available' },
                { name: 'Category' },
                { name: 'Last updated', sort: 'last_updated' },
                { name: 'Edit available quantity' }
            ],
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
                    code: 'ACC2',
                    name: 'Pineapple crownless',
                    package: '7 CT',
                    available: 6462020,
                    category: 'Fruits',
                    last_updated: '2021-02-03 19:49:33'
                },
                {
                    code: 'ACC3',
                    name: 'Banana Green',
                    package: '8 CT',
                    available: 8664948,
                    category: 'Fruits',
                    last_updated: '2021-02-05 08:28:36'
                },
                {
                    code: 'ACC4',
                    name: 'White Rice',
                    package: '21 CT',
                    available: 2592335,
                    category: 'Grains',
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
    box-sizing: border-box;
}

.container {
    max-width: 1140px;
    margin: 0 auto;
}

.subtitle {
    color: $color-dark;
}
</style>
