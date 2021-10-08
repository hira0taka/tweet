<template>
  <div class="wrapper">
    <h2 class="text-info">Twitter-Vue3</h2>
    <div class="content">
      <Form v-on:tweet-event="tweetAction" />
      <div style="margin-top: 20px">
        <Tweet
          v-for="Tweet in AllTweet"
          v-bind:TweetObj="Tweet"
          v-bind:key="Tweet.tweet_id"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import Tweet from "./components/Tweet.vue";

export default {
  name: "App",
  components: {
    Form,
    Tweet,
  },
  data() {
    return {
      AllTweet: Array.of({
        tweet_id: 0,
        tweet_body: "はじめてのツイート",
      }),
    };
  },
  methods: {
    tweetAction(TweetObj) {
      this.AllTweet.push(TweetObj);
    },
  },
};
</script>

<style>
.wrapper {
  width: 60%;
  margin: 20px auto;
}
.content {
  margin: 20px auto;
  width: 100%;
}
</style>
