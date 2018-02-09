<template>
    <div>
        <!--<ul v-if="posts && posts.length">-->
            <!--&lt;!&ndash;<li v-for="post in posts">&ndash;&gt;-->
                <!--&lt;!&ndash;<p><strong>{{post.title}}</strong></p>&ndash;&gt;-->
                <!--&lt;!&ndash;<p>{{post.body}}</p>&ndash;&gt;-->
            <!--&lt;!&ndash;</li>&ndash;&gt;-->
            <!--<p>{{posts}}</p>-->
        <!--</ul>-->

        <!--<ul v-if="errors && errors.length">-->
            <!--<li v-for="error in errors">-->
                <!--{{error.message}}-->
            <!--</li>-->
        <!--</ul>-->
        aa
    </div>
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
            axios.get('https://itunes.apple.com/lookup?amgArtistId=468749')
                .then(response => {
                    // JSON responses are automatically parsed.
                    this.posts = response
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