<template>
  <div>
    <div class="wrapper">
      <!-- ユーザー情報を渡すイベント -->
      <SelectUser v-on:selectUser-event="selectUser" />
      <div class="tweet-contents">
        <h2 class="text-success">Twitter-Vue3</h2>
        <div class="content">
          <!-- ユーザー情報をpropsで受け取る -->
          <Form v-on:tweet-event="tweetAction" v-bind:user="tweet_user" />
          <div style="margin-top:20px">
            <Tweet
              v-for="Tweet in AllTweet"
              v-bind:TweetObj="Tweet"
              v-bind:key="Tweet.tweet_id"
            />
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Form from "./components/Form.vue";
import Tweet from "./components/Tweet.vue";
import SelectUser from "./components/SelectUser.vue";

export default {
  name: "App",
  components: {
    Form,
    Tweet,
    SelectUser,
  },
  data() {
    return {
      AllTweet: Array.of(
        // 初回表示用のダミーデータ
        {
        tweet_id: 0,
        tweet_user: {
          user_id: "TestId",
          user_name: "ユーザー",
        },
        tweet_body: "はじめてのツイート",
      }
      ),

      // 初回ロード時にForm.vueにpropsとして渡し、selectUser()で上書きするためのデータ
      tweet_user: {
        user_id: "TestId",
        user_name: "ユーザー",
      },
    };
  },

  methods: {
    tweetAction(TweetObj) {
      this.AllTweet.push(TweetObj);
    },
    selectUser(user) {
      console.log(user);
      this.tweet_user = user;
    },
  },
};
</script>