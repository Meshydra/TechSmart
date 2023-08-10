<script>
    let categories = ['About Us', 'Contact Us']; // Define your categories
</script>
    
<nav class="bg-gray-800 text-white py-4">
    <div class="container px-4 flex items-center justify-between">
        <div class="text-xl font-bold">TechMart</div>
        <ul class="flex space-x-4">
            <li class="cursor-pointer hover:text-gray-300">
                <a href="/">Home</a>
            </li>
            {#each categories as category}
            <li class="cursor-pointer hover:text-gray-300">
                <a href="/category/{category}">{category}</a>
            </li>
            {/each}
        </ul>
    </div>
</nav>
