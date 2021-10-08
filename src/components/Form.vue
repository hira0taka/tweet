<template>
  <div class="form form-group">
    <textarea
    name="form"
    id=""
      v-model="TweetObj.tweet_body"
      rows="10"
      cols="5"
      class="form-control"
      placeholder="今なにしてる？"
    ></textarea>
    <br/>
    <button class="text-white bg-info" v-on:click="doTweet">
      ツイートする
    </button>
  </div>
</template>

<script>
export default {
  name: "Form",
  data() {
    return {
      TweetObj:{
        tweet_id:0,
        tweet_body:'',
      },
    }
  },
  methods: {
    doTweet(){
      this.TweetObj.tweet_id += 1
      const tweet = Object.assign({},this.TweetObj)
      this.$emit('tweet-event',tweet)
    },
  },
};
</script>
