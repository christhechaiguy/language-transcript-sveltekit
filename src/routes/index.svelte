<script lang="ts">
     import { onMount } from 'svelte'
	import { marked } from 'marked'
    import "carbon-components-svelte/css/white.css"
    // import "$lib/styles/fonts/Satoshi/css/satoshi.css"
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
    <p id="author">{author}</p>
    <h1>{title}</h1>
    <p id="date">{date}</p>
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
    .transcript-output p#author {
        font-weight: bold;
        text-transform: uppercase;
        opacity: 0.55;
        font-size: 14px;
    }
    .transcript-content {
        position: relative;
        margin-top: 1rem
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
        .input-el { display: none }
    }
</style>