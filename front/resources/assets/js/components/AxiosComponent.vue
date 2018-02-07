<template>
    <ul v-if="posts && posts.length">
        <li v-for="post in posts">
            <p><strong>{{post.title}}</strong></p>
            <p>{{post.body}}</p>
        </li>
    </ul>

    <ul v-if="errors && errors.length">
        <li v-for="error in errors">
            {{error.message}}
        </li>
    </ul>
</template>

<script>
    import axios from 'axios';

    export default {
        data() {
            return {
                posts: [],
                errors: []
            }
        },

        // Fetches posts when the component is created.
        created() {
            axios.get('')
                .then(response => {
                    // JSON responses are automatically parsed.
                    this.posts = response.data
                })
                .catch(e => {
                    this.errors.push(e)
                })

            // async / await version (created() becomes async created())
            //
            // try {
            //   const response = await axios.get('')
            //   this.posts = response.data
            // } catch (e) {
            //   this.errors.push(e)
            // }
        }
    }
</script>