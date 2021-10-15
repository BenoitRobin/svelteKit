<script>
    import Nav from "$lib/UI/Nav.svelte";
    import Footer from "$lib/UI/Footer.svelte";
</script>

<Nav />

<div class="main">
    <slot />
</div>


<Footer />


<style lang="scss">
    @import '../vars.scss';

    .main {
        height: 80vh;
        width: 70%;
        margin: $mL auto;
        background-color: $alt-bg-color;
        @include flexColumn;

        border-radius: calc($bor-rad *10);
    }
</style>