<template>
    <div class="backdrop" @click.self="closeModal">
        <div class="modal" :class="{sale: theme==='sale', dark: theme==='dark'}">
            <!-- <h1>{{ header }}</h1>
            <p>{{ text }}</p> -->
            <slot><h1>Default Content</h1></slot>
            <div class="actions">
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>
<!--  -->
<script>
    export default {
        props: [
            // "header",
            // "text",
            "theme"
        ],

        methods: {
            closeModal() {
                this.$emit("close")
            }
        }
    }
</script>

<style>
    .backdrop {
        top: 0;
        position: fixed;
        height: 100%;
        width: 100%;
        background-color: rgba(0,0,0,0.5);
        /* text-align: center; */
    }

    .modal {
        text-align: center;
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background-color: #fff;
        border-radius: 10px;
    }

    .modal h1 {
        color: #0000ff;
        margin: 20px 0;
    }

    .modal p {
        font-style: italic;
    }

    .modal .actions {
        margin: 15px;
    }

    .modal .actions a {
        text-decoration: none;
        margin: 5px;
        border: 1px solid #000;
        padding: 5px 10px;
        border-radius: 7px;
        color: #000;
        transition: all ease 300ms;
    }

    .modal .actions a:hover {
        background: #0000ff;
        border: none;
        color: #fff
    }

    .modal.sale {
        background-color: crimson;
        color: white;
    }

    .modal.sale h1 {
        color: yellow;  
    }

    .modal.sale .actions a {
        border: 1px solid #fff;
        color: #fff;
    }

    .modal.sale .actions a:hover {
        background: yellow;
        border: none;
        color: crimson;
        
    }

    .modal.dark {
        background-color: #000000;
        color: white;
    }

    .modal.dark h1 {
        color: yellow;
    }
    
    .modal.dark .actions a {
        border: 1px solid #fff;
        color: #fff;
    }

    .modal.dark .actions a:hover {
        background: yellow;
        border: none;
        color: #000;;
    }



    /* contact modal */
    .modal form {
        text-align: left;
        /* background: red; */
    }

    .modal form .field-container label {
        font-size: 16px;
    }

    .modal form .field-container input {
        width: 100%;
        padding: 10px;
        color: #000;
        margin-bottom: 15px;
        font-size: 16px;
        border: 1px solid #cccccc;
        font-weight: 100;
        border-radius: 7px;
        background: transparent;
    }

    .modal form .field-container input:focus {
        outline-color: #0000ff;
    }

    .modal form .field-container textarea {
        font-size: 16px;
        font-weight: 100;
        width: 100%;
        height: 150px;
        border: none;
        border: 1px solid #cccccc;
        background: transparent;
        color: #000;
        padding: 10px;
        border-radius: 7px;
    }

    .modal form .field-container textarea:focus {
        outline-color: #0000ff;
    }

    .modal form button.submit-btn {
        width: 100%;
        padding: 10px;
        background: #0000ff;
        color: #fff;
        border: none;
        border-radius: 7px;
        margin-top: 15px;
        transition: all ease 300ms;
        cursor: pointer;
    }

    .modal form button.submit-btn span.btn-text {
        font-weight: 700;
    }

    .modal form button.submit-btn:hover {
        opacity: .85;
    }



    /* sale mode */
    .modal form .field-container input,
    .modal form .field-container textarea {
        color: white;
        border: 1px solid #fff;
    }

    .modal form .field-container input:focus,
    .modal form .field-container textarea:focus {
        outline-color: yellow;
        /* border: 0; */
    }

    .modal form button.submit-btn {
        background: yellow;
        color: black;
    }

    ::-webkit-input-placeholder,
    ::-moz-placeholder,
    :-moz-placeholder,
    :-ms-input-placeholder {
        color: #fff;
    }

    ::-moz-focus-inner,
    ::-moz-focus-outer {
        outline-color: yellow;
    }

    /* dark mode */
    .modal.dark form .field-container input {
        /* border: none; */
        border: 1px solid #cccccc;
        background: transparent;
    }

    .modal.dark form button.submit-btn {
        background: yellow;
    }
</style>