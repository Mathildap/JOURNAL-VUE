<template>
    <form @submit="handleSubmit">
        <input
            type="text"
            placeholder="Header"
            id="heading"
            maxlength="150"
            size="20"
        />
        <input type="date" id="pickDate" />
        <input placeholder="Thankful for.." id="textArea" size="50" />
        <button>add</button>
    </form>
</template>

<script>
export default {
    name: 'Form',
    props: {
        post: {
            type: Object,
        },
    },
    methods: {
        handleSubmit(event) {
            this.$emit('save', event);
        },
    },
};
</script>

<style>
form {
    width: 80%;
    margin: 20px auto;
}
input {
    height: 30px;
    border: 0;
    margin-right: 3px;
    font-family: 'Playfair Display', Helvetica, serif;
    letter-spacing: 1px;
    padding: 0;
    padding-left: 3px;
    outline: 0;
}
button {
    padding: 6px 15px;
    border: 0;
    margin-left: 5px;
    background-color: rgb(77, 72, 72);
    color: white;
    font-family: 'Playfair Display', Helvetica, serif;
    letter-spacing: 1px;
}
button:hover {
    background-color: rgba(77, 72, 72, 0.719);
}
</style>
