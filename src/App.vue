<template>
    <main>
        <h1>One line a day</h1>
        <button class="newPostBtn" @click="newPostBtnHandler">new line</button>

        <section v-if="newPost == true">
            <Form @save="handleSubmit" />
        </section>

        <Posts :posts="posts" />
    </main>
</template>

<script>
import Form from './components/Form.vue';
import Posts from './components/Posts.vue';

export default {
    name: 'App',
    data() {
        return {
            posts: [],
            newPost: false,
            doUpdate: false,
        };
    },
    created() {
        this.posts = JSON.parse(localStorage.getItem('Posts'));
    },
    updated() {
        this.doUpdate = false;
    },
    components: { Form, Posts },
    methods: {
        newPostBtnHandler() {
            this.newPost = !this.newPost;
        },
        handleSubmit(event) {
            event.preventDefault();

            if (localStorage.getItem('Posts') == null) {
                let posts = [];
                posts.push({
                    heading: event.target.heading.value,
                    pickDate: event.target.pickDate.value,
                    textArea: event.target.textArea.value,
                });

                localStorage.setItem('Posts', JSON.stringify(posts));
            } else {
                let savedPosts = JSON.parse(localStorage.getItem('Posts'));
                savedPosts.push({
                    heading: event.target.heading.value,
                    pickDate: event.target.pickDate.value,
                    textArea: event.target.textArea.value,
                });

                localStorage.setItem('Posts', JSON.stringify(savedPosts));
            }
            this.newPost = !this.newPost;
            this.doUpdate = true;

            if (this.doUpdate === true) {
                this.posts = JSON.parse(localStorage.getItem('Posts'));
            }
        },
    },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display&display=swap');

body {
    background-color: rgb(250, 245, 242);
    font-family: 'Playfair Display', Helvetica, serif;
    color: rgb(18, 18, 18);
}
h1 {
    text-transform: uppercase;
    text-align: center;
    font-weight: 100;
    font-size: 35px;
    margin-top: 60px;
}
.newPostBtn {
    padding: 5px 15px;
    border: 0;
    background-color: rgb(77, 72, 72);
    color: white;
    font-family: 'Playfair Display', Helvetica, serif;
    font-size: 1.1em;
    letter-spacing: 1px;
    display: block;
    margin-left: 10%;
}
.newPostBtn:hover {
    background-color: rgba(77, 72, 72, 0.719);
}
</style>
