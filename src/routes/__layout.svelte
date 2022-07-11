<main>
    <div class="content-wrap">
        <slot />
    </div>
</main>

<style>
    /* :global(*) {
        font-family: 'Satoshi-Variable';
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

    @media print {
        main {
            padding: 0;
        }
    }
</style>