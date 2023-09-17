<template>
    <div class="card">
        <div class="card-header">Timeline</div>
        <div class="card-body">
            <post :tweets="tweets"></post>
            <hr />
            <div
                class="d-flex mb-3"
                v-for="(tweet, index) in tweets"
                :key="index"
            >
                <div class="flex-shrink-0">
                    <img src="https://placehold.it/64x64" alt="..." />
                </div>
                <div class="flex-grow-1 ms-3">
                    <h5>{{ tweet.user.name }}</h5>
                    {{ tweet.body }}
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import Post from "./Post.vue";
export default {
    data() {
        return {
            tweets: [],
        };
    },
    components: {
        Post,
    },
    mounted() {
        axios
            .get("tweets")
            .then((res) => {
                this.tweets = res.data;
            })
            .catch((err) => {
                console.log(err);
            });
    },
};
</script>
