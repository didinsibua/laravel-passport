<template>
    <div>
        <form action="#" @submit.prevent="post">
            <div class="form-group">
                <textarea rows="2" cols="30" class="form-control" v-model="body"></textarea>
            </div>
            <button type="submit" class="btn btn-primary">Post</button>
        </form>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                body: null
            }
        }, 
        props: {
            tweets: Array
        }, 
        methods: {
            post() {
                axios.post('/tweets', {
                    body: this.body 
                }).then(response => {
                    this.tweets.unshift(response.data);
                    this.body = null;
                })
                .catch(err => {
                    console.error(err); 
                })
            }
        },
    }
</script>