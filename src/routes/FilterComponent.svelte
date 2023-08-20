<script>
    import products from "../stores/products";

    let category = '';
    let minPrice = '';
    let maxPrice = '';

    function applyFilters() {
        const filter = {
            category: category,
            minPrice: minPrice,
            maxPrice: maxPrice
        };

        // Apply filters to the product list
        const filteredProducts = $products.filter(product => {
            // Apply category filter if set
            if (filter.category && product.category !== filter.category) {
                return false;
            }

            // Apply price range filter if set
            if (
                (filter.minPrice && product.price < filter.minPrice) ||
                (filter.maxPrice && product.price > filter.maxPrice)
            ) {
                return false;
            }

            return true;
        });

        // Call the function provided by the ProductListComponent to update filteredProducts
        applyFilters(filteredProducts);
    }
</script>

<div class="p-6 bg-gradient-to-r shadow-lg">
    <div class="grid grid-cols-1 md:grid-cols-3 gap-4">
        <input
            class="p-3 rounded-lg bg-gray-800 text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
            bind:value={category}
            placeholder="Category"
        >
        <input
            class="p-3 rounded-lg bg-gray-800 text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
            bind:value={minPrice}
            type="number"
            placeholder="Min Price"
        >
        <input
            class="p-3 rounded-lg bg-gray-800 text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
            bind:value={maxPrice}
            type="number"
            placeholder="Max Price"
        >
    </div>
    <button
        class="mt-4 py-2 px-4 bg-blue-600 hover:bg-blue-700 text-white rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500"
        on:click={applyFilters}
    >
        Apply Filters
    </button>
</div>

