<main>
    <div class="content-wrap">
        <slot />
    </div>
</main>

<style>
    /* :global(*) {
        font-family: 'Satoshi-Variable', sans-serif !important;
    } */

    :global(h1) {
        font-weight: 500 !important;
        font-family: 'Satoshi-Variable', sans-serif !important;
    }

    :global(p) {
        /* font-family: 'Noto Sans', sans-serif !important; */
        font-weight: 400 !important;
    }

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
        :global(*) {
            color: #000000;
        }
        main {
            padding: 0;
        }
    }
</style>