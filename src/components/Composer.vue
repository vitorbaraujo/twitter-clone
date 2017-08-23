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
        <button :disabled="tweetIsEmpty">Tweet</button>
      </div>
    </div>
  </div>
</template>

<script>
  export default {
    name: 'composer',
    data() {
      return {
        tweet: '',
      };
    },
    computed: {
      tweetIsEmpty() {
        return this.tweet.length === 0;
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
  }

  .composer > .content > .tweet-btn > button {
    float: right;
  }
</style>
