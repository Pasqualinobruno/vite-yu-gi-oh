<script>
export default {
    name: 'AppHeader',
}
</script>
<template>
    <header>
        <div class="container">
            <img width="150px" height="50px"
                src="https://images.ygoprodeck.com/images/assets/ygoprodeck_header_logo.png?v=1.13" alt="">
            <h1>Yu-Gi-Oh! Api</h1>
        </div>
    </header>
</template>
<style scoped>
header {
    background-color: var(--yu-gi-oh-light);
    padding: 1rem;

    & .container {
        display: flex;
        flex-wrap: wrap;
        gap: 1rem;
        align-items: center;
    }
}
</style>