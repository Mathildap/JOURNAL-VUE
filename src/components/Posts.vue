<template>
    <section class="posts-container">
        <article v-for="post in even(posts)" :key="post.heading">
            <div class="header-date">
                <h3>{{ post.heading }}</h3>
                <p>{{ post.pickDate }}</p>
            </div>
            <p>{{ post.textArea }}</p>
            <hr />
        </article>
    </section>
</template>

<script>
import posts from '../App.vue';

export default {
    name: 'Posts',
    props: {
        posts,
    },
    methods: {
        even(arr) {
            if (arr != null) {
                return arr.slice().sort((a, b) => {
                    return new Date(b.pickDate) - new Date(a.pickDate);
                });
            }
        },
    },
};
</script>

<style>
.posts-container {
    width: 80%;
    margin: 20px auto;
    color: #2c3e50;
}
.header-date {
    display: flex;
    justify-content: space-between;
}
h3 {
    font-size: 1em;
    text-transform: uppercase;
    letter-spacing: 1px;
}
</style>
