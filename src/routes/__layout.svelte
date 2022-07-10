<main>
    <div class="content-wrap">
        <slot />
    </div>
</main>

<style>
    /* :global(*) {
        font-family: 'Satoshi-Variable';
    }

    :global(h1) {
        font-weight: 800;
    } */

    main {
        padding: 5rem 0;
    }

    .content-wrap {
        max-width: 1140px;
        width: 100%;
        padding: 0 15px;
        margin: 0 auto;
    }
</style>