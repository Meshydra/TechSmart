<script>
    import { onMount } from 'svelte';
    import products from '../stores/products'; // Adjust the path to your store

    onMount(async () => {
        try {
            const response = await fetch('https://dummyjson.com/products');
            if (!response.ok) {
                throw new Error('Failed to fetch products');
            }
            const data = await response.json();
            products.set(data.products);
        } catch (error) {
            console.error('Error fetching products:', error);
        }
    });
</script>

{#if $products.length > 0}
    <ul>
        {#each $products as product (product.id)}
            <div class="border p-4 rounded-lg shadow-md">
                <img src={product.thumbnail} alt={product.title} class="w-full h-auto mb-2" />
                <h2 class="text-lg font-semibold">{product.title}</h2>
                <p class="mt-2 text-gray-600">${product.price}</p>
            </div>
        {/each}
    </ul>
{:else}
    <p>Loading products...</p>
{/if}
