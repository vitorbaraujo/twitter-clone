<template>
  <div>
    <composer @push="addTweet"></composer>

    <div class="timeline">
      <div class="header">
        <h4>Timeline</h4>
      </div>

      <div class="tweets-list">
        <div v-for="tweet in tweetsList" class="tweet-content">
          <p>{{ tweet }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
  import Composer from './Composer';

  export default {
    name: 'timeline',
    data() {
      return {
        tweetsList: [],
      };
    },
    components: {
      composer: Composer,
    },
    methods: {
      addTweet(event) {
        this.tweetsList.push(event.tweet);
      },
    },
  };
</script>

<style>
  .timeline {
    background-color: white;
    margin-top: 20px;
    margin-left: 30%;
    border: 0.5px solid rgba(0,0,0,.1);
    border-bottom: none;
    width: 40%;
  }

  .timeline > .tweets-list {
    background-color: #f4f4f4 !important;
    overflow: auto;
  }

  .timeline > .tweets-list p {
    text-align: left;
    margin-left: 5%;
  }

  .tweet-content {
    height: 100%;
    border-bottom: 1px solid rgba(0,0,0,.1);
  }
</style>
