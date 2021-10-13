<template>
  <div class="card">
    <div class="card-header">
      {{ TweetObj.tweet_id }}
    </div>
    <div class="card-Body">
      <div class="card-text">
        <p class="body">{{ TweetObj.tweet_body }}</p>
        <hr />
        <div class="body">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            width="16"
            height="16"
            fill="currentColor"
            class="bi bi-heart"
            viewBox="0 0 16 16"
            v-on:click="document"
          >
            <path
              d="m8 2.748-.717-.737C5.6.281 2.514.878 1.4 3.053c-.523 1.023-.641 2.5.314 4.385.92 1.815 2.834 3.989 6.286 6.357 3.452-2.368 5.365-4.542 6.286-6.357.955-1.886.838-3.362.314-4.385C13.486.878 10.4.28 8.717 2.01L8 2.748zM8 15C-7.333 4.868 3.279-3.04 7.824 1.143c.06.055.119.112.176.171a3.12 3.12 0 0 1 .176-.17C12.72-3.042 23.333 4.867 8 15z"
            />
          </svg>
          {{ like }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Tweet",
  props: {
    TweetObj: Object,
  },
  data() {
    return {
      like: 0,
    };
  },
  methods: {
    document() {
      this.like++;
    },
  },
};
</script>

<style>
.card {
  margin-top: 17px;
}
.body {
  margin: 15px;
}
</style>