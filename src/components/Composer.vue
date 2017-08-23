<template>
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
        <button :disabled="tweetIsOutOfRange">Tweet</button>
      </div>
    </div>

    <!-- <p>The value of <strong>tweet</strong> is: {{ tweet }}</p>
    <p>The length of <strong>tweet</strong> is: {{ tweet.length }}</p>
    <p>The length of <strong>charactersRemaining</strong> is: {{ charactersRemaining }}</p>
    <p>The length of <strong>tweetIsOutOfRange</strong> is: {{ tweetIsOutOfRange  }}</p> -->
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
  };
</script>

<style>
  .composer {
    margin-left: 30%;
    width: 40%;
    border: 0.5px solid rgba(0,0,0,.1);
  }

  .composer > .header > h4 {
    margin: 10px 0;
  }

  .composer > .content {
    background-color: #f4f4f4 !important;
    padding-top: 10px;
    overflow: auto;
    padding-right: 5%;
    padding-bottom: 10px;
  }

  .composer > .content > .tweet-area {
    display: block;
    height: 100%;
    overflow: auto;
  }

  .composer > .content > .tweet-area > textarea {
    border-color: rgba(0,0,0,.1);
    width: 90%;
    float: right;
  }

  .composer > .content > .tweet-btn {
    padding-top: 10px;
    float: right;
  }

  .composer > p {
    text-align: left;
    margin-left: 5%;
  }

  .light-red {
    color: red;
  }

  .dark-red {
    color: #801515;
  }
</style>
