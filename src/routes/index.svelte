<script lang="ts">
     import { onMount } from 'svelte'
	import { marked } from 'marked'
    import "carbon-components-svelte/css/white.css"
    import "$lib/styles/fonts/Satoshi/css/satoshi.css"
    import {
    Form,
    FormGroup,
    Button,
    TextInput,
    TextArea,
    DatePicker,
    DatePickerInput
    } from "carbon-components-svelte";


	let title = '';
	let date = '';
	let author = '';
	let content = '';

    function print() {
        window.print()
    }

    // onMount(() => {
    //     $: transcriptTitle = data.title
    // }
    // function submitTranscript(e) {
    //     // e.preventDefault();
    //     const formData = new FormData(e.target);
    //     const data = {};
    //     for (let field of formData) {
    //         const [key, value] = field;
    //         data[key] = value;
    //     }
    //     console.log(data)
    // }

</script>
<div class="transcript-output">
    {#if content != ''}
        <div id="btn-print">
            <Button on:click={print}>Print Transcript</Button>
        </div>
    {/if}
    <p id="details">
        <span id="author">{author}</span>
        {#if author != '' && date != ''}
        <span> | </span>
        {/if}
        <span id="date">{date}</span>
    </p>
    <h1>{title}</h1>
    
    <div class="transcript-content">
        {@html marked(content)}
    </div>
</div>

<div class="input-el">
    <TextInput labelText="Title" placeholder="Transcript Title" bind:value={title} />
    <DatePicker datePickerType="single" on:change bind:value={date}>
        <DatePickerInput labelText="Published Date" placeholder="mm/dd/yyyy" />
    </DatePicker>
    <TextInput labelText="Author" placeholder="Transcript Author" bind:value={author} />
    <TextArea labelText="Content" placeholder="Transcript Content" bind:value={content} />
    <!-- <Button>Primary button</Button> -->
</div>

<style>
    .input-el {
        display: grid;
        gap: 2rem 0;
        grid-template-columns: 1fr;
        grid-template-rows: 1fr;
        padding-top: 2rem;
    }
    .transcript-output p#details {
        font-family: 'Satoshi-Variable', sans-serif !important;
        font-weight: bold;
        text-transform: uppercase;
        opacity: 0.55;
        font-size: 14px;
        margin-top: 2rem;
        margin-bottom: 0.85rem;
        font-weight: 700 !important;
    }
    .transcript-content {
        position: relative;
        margin-top: 1.5rem
    }
    /* .transcript-content:before {
        content: '';
        position: absolute;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-image: linear-gradient(#000 1px, transparent 1px);
        background-size: 100% 24px;
        z-index: -1;
    } */
    .transcript-content :global(p) {
        margin-bottom: 2rem;
        line-height: 3;
    }
    @media print {
        .input-el, #btn-print { display: none }
    }
</style>