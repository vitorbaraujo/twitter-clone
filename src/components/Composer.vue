<template>
  <div>
    <div class="composer">
      <div class="header">
        <h4>Compose new Tweet</h4>
      </div>
      <div class="content">
        <div class="tweet-area">
          <textarea rows="3" v-model="tweet"/>
        </div>
        <div class="tweet-btn">
          <span v-bind:class="[{ 'light-red' : lessThanTen, 'dark-red' : lessThanTwenty }]">{{ charactersRemaining }}</span>
          <button :disabled="tweetIsOutOfRange" @click="emitTweet()">Tweet</button>
        </div>
      </div>

      <!-- <p>The value of <strong>tweet</strong> is: {{ tweet }}</p>
      <p>The length of <strong>tweet</strong> is: {{ tweet.length }}</p>
      <p>The length of <strong>charactersRemaining</strong> is: {{ charactersRemaining }}</p>
      <p>The length of <strong>tweetIsOutOfRange</strong> is: {{ tweetIsOutOfRange  }}</p> -->
    </div>
  </div>
</template>

<script>
  const MAX_TWEET_LENGTH = 140;

  export default {
    name: 'composer',
    data() {
      return {
        tweet: '',
      };
    },
    computed: {
      tweetIsOutOfRange() {
        return this.charactersRemaining === MAX_TWEET_LENGTH || this.charactersRemaining < 0;
      },
      charactersRemaining() {
        return MAX_TWEET_LENGTH - this.tweet.length;
      },
      lessThanTwenty() {
        return this.charactersRemaining <= 20 && this.charactersRemaining > 10;
      },
      lessThanTen() {
        return this.charactersRemaining <= 10;
      },
    },
    methods: {
      emitTweet() {
        this.$emit('push', { tweet: this.tweet });
        this.tweet = '';
      },
    },
  };
</script>
