<template>
  <div class="form form-group">
    <input type="text" v-model="TweetObj.tweet_id" class="form-control" placeholder="user name">
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
        tweet_id:'',
        tweet_body:'',
      },
    }
  },
  methods: {
    doTweet(){
      // 第一引数を無名オブジェクト指定すると、TweetObjをコピーした内容の新規オブジェクトを作成できる
      const tweet = Object.assign({},this.TweetObj)
      this.$emit('tweet-event',tweet)
    },
  },
};
</script>
